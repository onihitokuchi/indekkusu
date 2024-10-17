## Debian/Ubuntu

1. First make sure you have the gpg command, and otherwise install it via:

   ```sh
   sudo apt install -y gpg
   ```

2. Then install eza via:
   ```sh
   sudo mkdir -p /etc/apt/keyrings
   wget -qO- https://raw.githubusercontent.com/eza-community/eza/main/deb.asc | sudo gpg --dearmor -o /etc/apt/keyrings/gierens.gpg
   echo "deb [signed-by=/etc/apt/keyrings/gierens.gpg] http://deb.gierens.de stable main" | sudo tee /etc/apt/sources.list.d/gierens.list
   sudo chmod 644 /etc/apt/keyrings/gierens.gpg /etc/apt/sources.list.d/gierens.list
   sudo apt update
   sudo apt install -y eza
   ```
