# nix-config

### My NixOS Configuration

This is my initial attempt at creating some nix configurations for my own personal use. Feel free to use this repo as well, though I suspect there are better ones out there.

## From scratch NixOS install

1. Generate ssh keys
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

2. Add ssh keys them to your github account with Github CLI
```bash
nix-shell -p gh 

gh auth login -h github.com -s admin:public_key

gh ssh-key add ~/.ssh/id_ed25519.pub --type authentication --title "key name"
```

3. Clone the repo
```bash
nix-shell -p git --command "git clone git@github.com:BradHarris/nix-config.git $HOME/nix-config"
```

4. Rebuild NixOS
```bash
sudo nixos-rebuild switch -I nixos-config=$HOME/nix-config/configuration.nix
```

5. Logout and login to ensure docker rootless works and certain envs are correctly loaded