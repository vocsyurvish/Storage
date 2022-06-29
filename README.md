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

### Share Temp Directory...
###### The temp directory here `storage\emulated\0\Android\data\YOUR_PACKAGE_NAME\cache\`

```java
ContextWrapper contextWrapper = new ContextWrapper(BooksActivity.this);
File file = new File(contextWrapper.getExternalCacheDir() + "/" + IMAGE_NAME + ".png");

// operation on "file" here...

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


### All files comand and its path

| Command of Path [CODE] | Output Path |
| :--- | :--- |
| Environment.getDownloadCacheDirectory() | /data/cache |
| Environment.getExternalStorageDirectory() | /storage/emulated/0 |
| wrapper.getExternalCacheDirs()[0] | /storage/emulated/0/Android/data/YOUR_PACKAGE/cache |
| wrapper.getExternalMediaDirs()[0] | /storage/emulated/0/Android/media/YOUR_PACKAGE |
| wrapper.getFilesDir()  | /data/user/0/YOUR_PACKAGE/files |
| getApplicationContext().getCacheDir() | /data/user/0/YOUR_PACKAGE/cache |
| getApplicationContext().getFilesDir() | /data/user/0/YOUR_PACKAGE/files |
