# OS, System und Tools
## Hostname setzen

Der Hostname des Systems muss gesetzt werden. Dieser Wert wird von vielen Konfig Tools ausgelesen.

```bash
echo "mail.ra-gas.de" | tee /etc/hostname
```

## Zeit
### NTP Installation

```bash
apt install ntp
```

### Zeitzone konfigurieren

```bash
dpkg-reconfigure tzdata
```


# Installation Tools
## Tmux

```bash
apt install tmux
```

## [optional] Fish Shell

Ich bevorzuge die fish Shell da diese in der default Konfiguration sehr sinnvolle Features besitzt.

```bash
apt install fish
```

```bash
chsh -s /usr/bin/fish
fish
```

### [optional] Prompt der Fish Shell

Ich verändere an der Fish Shell Installation nichts. Das ist gerade das Tolle an dieser Shell, sie ist per default cool.

Das hat aber den Nachteil das alle Prompt's, auch die via SSH, gleich aussehen. Die bash/zsh/sh Shell haben dafür die Umgebungsvariable `$PS1` (Infos darüber findet das [Netz](https://www.heise.de/ct/hotline/Linux-Bash-Prompt-veraendern-3268603.html)).
Die Fish Shell nutzt Anstelle von `$PS1` eine Funktion mit dem Namen `fish_prompt`. Hier ist ein Beispiel:

```bash
# cat ~/.config/fish/config.fish
function fish_prompt
  echo -n "hostname.tld" (pwd) '# '
end
```

Die Anleitung unter [https://fishshell.com/docs/current/tutorial.html#tut_prompt](https://fishshell.com/docs/current/tutorial.html#tut_prompt) weis mehr darüber.

## Vim mit spf13 Addons

```bash
apt install vim-scripts curl git
```

```bash
curl http://j.mp/spf13-vim3 -L -o - | sh
```

## Rust und Tools

Rust ist meine Standardwaffe und darf auf keinen Server mehr fehlen.

```bash
curl https://sh.rustup.rs -sSf | sh -s -- --default-toolchain nightly -y
```

```bash
echo "set PATH "\$HOME/.cargo/bin" \$PATH;" >>.config/fish/config.fish
source .config/fish/config.fish
```

Zudem bringt Rust coole Tools hervor. Hier installieren wir 2 von diesen. Sie ersetzen `grep` und `find`.

```bash
apt install build-essential
```

```bash
# `grep` Erstaz
cargo install ripgrep
# `find` Ersatz
cargo install --git https://github.com/sharkdp/fd
```

# Neustart
Nach dieser Basis Konfiguration wird das System einmal neu gestartet.

```bash
reboot
```


[debian]: http://debian.org/



<!-- TODO: Alle Tools in Unterseiten packen. Mit einer Einleitung das die [optional] Punkte ruhig übersprungen werden können. -->
