Here is the information formatted in **Markdown**:

```markdown
# Table of Contents
1. [Changing Commit Messages](#changing-commit-messages)
2. [Removing Credentials from Git on Local Machine](#removing-credentials-from-git-on-local-machine)
   - [Using Git Credential Helper](#using-git-credential-helper)
   - [Using the Git Configuration File](#using-the-git-configuration-file)
   - [Using Credential Manager for Windows](#using-credential-manager-for-windows)

---

## 1. Changing Commit Messages
You can change commit messages using interactive rebase:
- Use `git rebase -i --root` to edit all commits from the root.
- Use `git rebase -i <commit_hash>` to edit a specific commit.

## 2. Removing Credentials from Git on Local Machine

### 2.1. Using Git Credential Helper
- **Clear all cached credentials**: 
    ```sh
    git credential-cache exit
    ```
- **Remove specific credentials**: Edit the `.git-credentials` file (location depends on OS):
  - Windows: `C:\Users\<YourUsername>\.git-credentials`
  - macOS/Linux: `~/.git-credentials`

### 2.2. Using the Git Configuration File
- Open the Git configuration file:
    ```sh
    ~/.gitconfig or C:\Users\<YourUsername>\.gitconfig
    ```
- Look for the sections with credential information and remove or comment them out:
    ```sh
    [credential]
        helper = store
    [user]
        name = yourusername
        email = youremail@example.com
    ```

### 2.3. Using Credential Manager for Windows (GCM)
1. Open **Control Panel**.
2. Navigate to **User Accounts** > **Credential Manager**.
3. Under **Windows Credentials**, locate the Git-related credentials.
4. Click on the credentials and select **Remove**.
```
