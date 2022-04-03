# ftp-action

Automate copying your files via ftp using this GitHub action. This command is fork of sebastianpopp/ftp-action with customizable LFTP command.

## Example usage

```
name: Deploy via ftp
on: push
jobs:
  deploy:
    name: Deploy
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Upload ftp
      uses: sebastianpopp/ftp-action@releases/v2
      with:
        host: ${{ secrets.FTP_SERVER }}
        user: ${{ secrets.FTP_USERNAME }}
        password: ${{ secrets.FTP_PASSWORD }}
        command: "mirror"
        localDir: "dist"
        remoteDir: "www"
        options: "--delete --asci"
```

## Input parameters

Input parameter | Description | Required | Default
--- | --- | --- | ---
host | FTP server name | Yes | N/A
user | FTP username | Yes | N/A
password | FTP password | Yes | N/A
command | LFTP command | No | "mirror"
localDir | The local directory to copy | No | .
remoteDir | The remote directory to copy to | No | .
forceSsl | Force SSL encryption | No | false
options | Mirror command options | No | "--reverse --continue --dereference"
