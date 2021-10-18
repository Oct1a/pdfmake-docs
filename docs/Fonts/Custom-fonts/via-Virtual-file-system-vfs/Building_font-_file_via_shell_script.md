## 关于在客户端使用自定义字体的完整描述，请阅读这篇文章

如果你不想安装gulp 或者刚刚下载了pdfMake，想在客户端使用自定义字体，你也可以用`bash-script`生成`vfs_fonts.js`。

```sh
#!/bin/sh

if [ -t 1 ]; then
	target="vfs_fonts.js"
else
	target="/dev/stdout"
fi

(
	echo "this.pdfMake = this.pdfMake || {}; this.pdfMake.vfs = {"
	for file in "$@"; do
		file=$1
		filename=$(basename $file)
		filecontent=$(base64 -w 0 $file)
		shift
		echo "\"${filename}\":\"${filecontent}\""
		if [ "$#" -gt 0 ]; then
			echo ","
		fi
	done
	echo "};"
) > "$target"
```

如何使用脚本:

```sh
script.sh font1.ttf font2.ttf font3.ttf
```
如果你使用的是Mac，你需要修改这一行
```sh
		filecontent=$(base64 -w 0 $file)
```
将`-w` 更改为`-b`
```sh
		filecontent=$(base64 -b 0 $file)
```
GNU coreutils的base64似乎与苹果的base64不同，它有一个参数（防止换行的）。