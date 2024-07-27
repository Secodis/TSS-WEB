# {{site.TITLE_IMPL_FILEUPLOADS}}

## 1. Authentication
All file uploads SHOULD be authenticated by the user on the server-side (= function only available within the authenticated user area) and MUST implement suitable controls to preventing denial of service attacks if available to not authenticated users.

## 2. Storage
1. Uploaded files SHOULD be stored to a database.
2. In case uploaded files are required to be stored on a file system, the implementation MUST be according to the following requirements:
3. Uploaded files MUST be stored in an access protected directory that is not accessible from external (e.g. stored outside of the web & document root). For applications with ***assurance class >= [HIGH]***, uploaded files SHOULD be stores in a user-specific directory.
4. File uploads MUST be saved with restrictive permissions (e.g. in case of Unix-based systems `chmod 0600`).
5. Uploaded files MUST NOT be executable.
6. Uploaded files MUST be stored as a new file with unique filename that is not user-specified.

## 3. Limitation
1. The size of uploaded files MUST be restricted to a reasonable maximum (e.g. 5 MB).
2. The number of files that are allowed to be uploaded SHOULD be restricted to a reasonable value (e.g. 8 files from one user per hour and user or IP address).

## 4. Validation
1. File types that may consist of executable code (e.g. `.html`, `.js` or `.exe`) MUST be prevented from being uploaded.
2. File type validation MUST be executed  based on a whitelisting approach where only safe file types are allowed.
3. File type validation MUST be executed on file extension and MIME type.
4. For applications with ***assurance class >= [HIGH]***, the file type SHOULD be verified with suitable tools or APIs based on its actual content (e.g. you could perform image operations like `getImageSize()` on an expected image file).

## 5. Sanitization
Uploaded files from untrusted sources (e.g. over the Internet) with potentially executable content SHOULD be

1. sanitized of executable code (e.g. macros in MS Word files) and
2. analyzed with an antivirus (AV) solution for potential malware infections. Files MUST be rejected or sent to quarantine in cases of a positive finding.[^1]

## 6. Downloads
1. File downloads SHOULD be carried out from a separate origin (e.g. `files.example.com`), to prevent the impact of executable script code that they may contain.
2. File downloads SHOULD always be protected with relevant HTTP security headers, e.g. to prevent MIME Type sniffing in browsers (see [{{site.TITLE_IMPL_HTTPHEADERSEC}}]({{site.URL_IMPL_HTTPHEADERSEC}})).
3. Filenames MUST be properly encoded before written into response header when user-controlled in order to preventing Reflected File Downloads (RFD).

[^1]: This function can be tested with the EICAR test file ([www.eicar.org](www.eicar.org))
