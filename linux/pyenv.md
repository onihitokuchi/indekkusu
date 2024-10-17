```sh
# These system libraries are needed to compile Python.
sudo apt-get install -y build-essential

# Required
sudo apt-get install -y \
  libffi-dev \
  libreadline-dev \
  libssl-dev \
  zlib1g-dev \
  tk-dev

# Optional (recommended)
sudo apt-get install -y \
  libbz2-dev \
  liblzma-dev \
  libsqlite3-dev
```

```sh
 curl https://pyenv.run | bash

```

```zsh
export PYENV_ROOT="$HOME/.pyenv"
[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```

mkdir example/{projA,projB}
echo "3.7.1" > ./example/projA/.python-version
echo "3.10.5" > ./example/projB/.python-version
