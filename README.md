# Storage Utility

### Listout Files...

```java
public void listOutFiles(File basePath){
    File[] files = basePath.listFiles();
        if (files != null) {
            for (File file : files) {
                // write your logic here...
            }
        }
}
```

### Delete Files...

```java
public static void deleteMedia(File fileOrDirectory) {
        if (fileOrDirectory.isDirectory())
            for (File child : fileOrDirectory.listFiles())
                deleteMedia(child);
        fileOrDirectory.delete();
}
```
