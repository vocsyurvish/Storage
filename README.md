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

### Fileprovider Authority

- in Manifest.xml
```xml
<provider
      android:name="androidx.core.content.FileProvider"
      android:authorities="${applicationId}.provider"
      android:exported="false"
      android:grantUriPermissions="true">
      <meta-data
          android:name="android.support.FILE_PROVIDER_PATHS"
          android:resource="@xml/provider_paths" />
</provider>
```
- in xml folder as a "provider_paths.xml"
```xml
<?xml version="1.0" encoding="utf-8"?>
<paths>
    <external-path
        name="external_files"
        path="." />
</paths>
```
