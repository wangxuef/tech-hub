#### 写文件：

##### FileOutputStream 写文件，FileInputStream读取文件

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

**FileWriter**

```java
public static void writeUsingFileWriter(String outFilePath, String filePath) {
    FileReader fr = null;
    FileWriter fwr = null;
    char[] buffer = new char[1024];
    try {
        fr = new FileReader(filePath);
        fwr = new FileWriter(outFilePath);
        int i = 0;
        while ((i = fr.read(buffer)) != -1) {
            fwr.write(buffer);
        }
    } catch (FileNotFoundException e) {
        e.printStackTrace();
    } catch (IOException e) {
        e.printStackTrace();
    } finally {
        try {
            if (fr != null) {
                fr.close();
            }
            if (fwr != null) {
                fwr.close();
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

##### BufferedReader 读取文件，BufferedWriter写文件

```java
public static void writeUsingBufferedWriter(String outFilePath, String filePath) {
    BufferedReader br = null;
    BufferedWriter bwr = null;
    try {
        br = new BufferedReader(new FileReader(filePath));
        bwr = new BufferedWriter(new FileWriter(outFilePath));
        String str = null;
        while ((str = br.readLine()) != null) {
            bwr.write(str);
        }
    } catch (FileNotFoundException e) {
        e.printStackTrace();
    } catch (IOException e) {
        e.printStackTrace();
    } finally {
        try {
            if (br != null) {
                br.close();
            }
            if (bwr != null) {
                bwr.close();
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

##### 逐行写文件

```java
public static void writeFile() throws IOException {
    File fout = new File("dir1/file1");
    FileOutputStream fos = new FileOutputStream(fout);
    BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(fos));
    for (int i = 0; i < 10; i++){
        bw.write("something");
        bw.newLine();
    }
    bw.close();
}

public static void writeFile() throws IOException {
	File fout = new File("dir1/file1");
	FileWriter fw = new FileWriter(fout);
	for (int i = 0; i < 10; i++) {
		fw.write("something" + System.getProperty("line.separator"));
	}
	fw.close();
}
```



