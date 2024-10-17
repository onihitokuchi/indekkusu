```sh
######
# Add pyenv config to $HOME/.bashrc
# WARNING: Dangerous command, make sure to back up
########################
cat <<'EOF' >> ~/.bashrc

# pyenv configuration
export PATH="$HOME/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
EOF
```
