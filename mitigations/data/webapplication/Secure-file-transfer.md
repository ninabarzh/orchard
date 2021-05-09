# Secure file transfer

* Verify the file type without trusting the Content-Type header, which can be spoofed.
* Enforce file name length and size limit, and change the file name while hosting it on a server.
* Only allow extensions that are required for the application's functionality. If files are publicly available, use handler mapping to map ID to filename within the application.
* If possible, run files through a sandbox or antivirus.

