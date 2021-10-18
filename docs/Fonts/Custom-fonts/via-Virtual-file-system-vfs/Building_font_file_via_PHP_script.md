## 关于在客户端使用自定义字体的完整描述，请阅读这篇文章。

如果你不想去安装gulp或刚刚下载了pdfMake 想在客户端使用自定义字体, 你可以创建一个vfs_fonts.js 也是可以用PHP脚本来实现的。<br>
把下面的代码放在服务器上的一个文件中，与你想引入的字体文件放在同一个目录中，然后在浏览器中查看. 使用参数 `?tofile` 在URL中写入输出到服务器上同一目录下的 `"vfs_fonts.js"`，否则会在浏览器窗口中输出，供你复制/粘贴。

```php
<?php

    $output = "this.pdfMake = this.pdfMake || {}; this.pdfMake.vfs = {";
    $phpDir=dir('.');
    while (($file=$phpDir->read())!==false) {
        if ($file!='..' && $file!='.' && $file!='makefont.php' && $file!='vfs_fonts.js') {
            $output .= '"';
            $output .= $file;
            $output .= '":"';
            $output .= base64_encode(file_get_contents($file));
            $output .= '",';
        }
    }
    $output=substr($output,0,-1);
    $output .= "}";

    if (isset($_REQUEST['tofile'])) {
	$fh = fopen('vfs_fonts.js', 'w') or die("CAN'T OPEN FILE FOR WRITING");
	fwrite($fh,$output);
	fclose($fh);
        echo 'vjs_fonts.js created';
    } else {
        echo $output;
    }
via Virtual file system (VFS)
```