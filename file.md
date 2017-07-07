#### 写文件：

**FileOutputStream 写文件，**FileInputStream读取文件

```java
public static void writeUsingStream(String outFilePath, String filePath) {
	FileOutputStream fout = null;
	FileInputStream fin = null;
	byte[] buffer = new byte[1024];
	try {
		fin = new FileInputStream(new File(filePath));
		fout = new FileOutputStream(new File(outFilePath));
		int i = 0;
		while ((i = fin.read(buffer)) != -1) {
			fout.write(buffer);
		}
	} catch (FileNotFoundException e) {
		e.printStackTrace();
	} catch (IOException e) {
		e.printStackTrace();
	} finally {
		try {
			if (fin != null) {
				fin.close();
			}
			if (fout != null) {
				fout.close();
			}
		} catch (IOException e) {
			e.printStackTrace();
		}
	}
}
```



