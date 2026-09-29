# Git
Check that Git is installed (`git --version`); if not, help the user install it. Then help the user set up their Git identity and the credential store so they aren't asked for a password on every pull:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global credential.helper store
```

The credentials are saved on the first successful `git pull`/`git clone` over HTTPS. Note: `store` keeps them in plain text in `~/.git-credentials`.

## GitLab: Personal Access Token
GitLab doesn't accept the account password over HTTPS, so ask the user to create a personal access token:

1. Sign in to GitLab (gitlab.com or the company's self-hosted instance).
2. Click the avatar (top left) → **Edit profile** → **Access tokens** (or open `https://<gitlab-host>/-/user_settings/personal_access_tokens`).
3. Click **Add new token**.
4. Fill in:
   - **Token name**: e.g. `laptop-dev`
   - **Expiration date**: pick one (GitLab may enforce a maximum)
   - **Scopes**: `read_repository` and `write_repository`
5. Click **Create personal access token**, then copy the token right away. GitLab shows it only once.
6. On the next `git clone`/`git pull` over HTTPS, enter the GitLab **username** as the username and the **token** as the password. The credential store remembers it.
