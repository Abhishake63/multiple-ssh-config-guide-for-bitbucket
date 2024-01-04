# Using Multiple Bitbucket Accounts on a Single Device

## Generate SSH Keys for Each Bitbucket Account

1. Generate SSH key for Software Company account:
   ```bash
   ssh-keygen -t ed25519 -b 4096 -C "john.doe@softwarecompany.com" -f ~/.ssh/softwarecompany
   ```

2. Add the generated public key (`softwarecompany.pub`) to the Bitbucket account's SSH settings.

3. Generate SSH key for Tech Company account:
   ```bash
   ssh-keygen -t ed25519 -b 4096 -C "john.doe@techcompany.com" -f ~/.ssh/techcompany
   ```

4. Add the generated public key (`techcompany.pub`) to the Bitbucket account's SSH settings.

## Configure SSH Config File

1. Open the SSH configuration file in a text editor:
   ```bash
   nano ~/.ssh/config
   ```

2. Add the following entries for each Bitbucket account:

   ```plaintext
   Host softwarecompany
     HostName bitbucket.org
     IdentityFile ~/.ssh/softwarecompany

   Host techcompany
     HostName bitbucket.org
     IdentityFile ~/.ssh/techcompany
   ```

## Cloning Repositories

When cloning repositories, replace the default host with the configured host:

- For Software Company:
  ```bash
  git clone git@softwarecompany:myworkspacesoftwarecompany/myrepo.git
  ```

- For Tech Company:
  ```bash
  git clone git@techcompany:myworkspacetechcompany/myanotherrepo.git
  ```

Ensure to replace `bitbucket.org` with the appropriate configured host. You're all set! This setup allows you to work with multiple Bitbucket accounts on a single device seamlessly.
```
