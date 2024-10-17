```sh
# dep
sudo apt-get install cmake pkg-config libfreetype6-dev libfontconfig1-dev libxcb-xfixes0-dev libxkbcommon-dev python3 scdoc gzip

# rust
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

rustup override set stable
rustup update stable

# repo
git clone https://github.com/alacritty/alacritty.git
cd alacritty

# build
cargo build --release

# Terminfo
sudo tic -xe alacritty,alacritty-direct extra/alacritty.info

# desktop entry
sudo cp target/release/alacritty /usr/local/bin # or anywhere else in $PATH
sudo cp extra/logo/alacritty-term.svg /usr/share/pixmaps/Alacritty.svg
sudo desktop-file-install extra/linux/Alacritty.desktop
sudo update-desktop-database

# Manual Page
sudo mkdir -p /usr/local/share/man/man1
sudo mkdir -p /usr/local/share/man/man5
scdoc < extra/man/alacritty.1.scd | gzip -c | sudo tee /usr/local/share/man/man1/alacritty.1.gz > /dev/null
scdoc < extra/man/alacritty-msg.1.scd | gzip -c | sudo tee /usr/local/share/man/man1/alacritty-msg.1.gz > /dev/null
scdoc < extra/man/alacritty.5.scd | gzip -c | sudo tee /usr/local/share/man/man5/alacritty.5.gz > /dev/null
scdoc < extra/man/alacritty-bindings.5.scd | gzip -c | sudo tee /usr/local/share/man/man5/alacritty-bindings.5.gz > /dev/null
```

---

sudo add-apt-repository ppa:aslatter/ppa
sudo apt update
sudo apt install alacritty
