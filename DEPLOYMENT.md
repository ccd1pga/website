# Deployment

This project is intended to be deployable from the terminal, instead of manually uploading files in Dreamweaver.

## Preferred Option: SSH/Rsync

If the Fasthosts package supports SSH access, use `rsync` because it can upload only changed files and can delete old files from the server when asked.

This hosting package has SSH/SFTP enabled. Fasthosts says website files should be uploaded to the `HTDOCS` folder, so the private local deployment settings use `htdocs/` as the remote path.

1. Copy the example environment file:

   ```sh
   cp deploy/fasthosts.env.example deploy/fasthosts.env
   ```

2. Edit `deploy/fasthosts.env` with the real server details from Fasthosts.

3. Build the website locally once the project has a build step.

4. Deploy:

   ```sh
   ./scripts/deploy-fasthosts.sh
   ```

## If Fasthosts Only Provides FTP

Some Fasthosts Webspace packages are managed through FTP accounts. If this account only has FTP/FTPS, use a dedicated sync tool such as `lftp` rather than the basic macOS FTP tooling.

The deployment script in this repository is set up for SSH/rsync first. If FTP is needed later, add an `lftp` version of the script after confirming:

- FTP host
- FTP username
- Remote web root folder
- Whether FTPS is required

Do not commit real FTP, SSH, or hosting passwords to this repository.

## Details Needed From Fasthosts

Find these in the Fasthosts Control Panel or hosting welcome email:

- Protocol available: SSH/SFTP
- Remote web root path: `htdocs/`
- Port number: `22`

The real host and username live in the ignored local file `deploy/fasthosts.env`.
