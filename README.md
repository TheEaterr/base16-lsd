# Base16 template for lsd

Base16 template to use with [lsd](https://github.com/lsd-rs/lsd), forked from [this repository](https://github.com/eilefsen/base16-lsd) and updated to use the proper format according to spec.

## Usage

The file to be updated using the template is `.config/lsd/colors.yaml`. Moreover, the option `color.theme` needs to be set to custom in `.config/lsd/config.yaml`.

### Home-manager

Using home manager and [base16.nix](https://github.com/SenchoPens/base16.nix), this repo can be used by adding it as an input in `flake.nix`:

```
base16-lsd = {
  url = "github:TheEaterr/base16-lsd";
  flake = false;
};
```

and then in your home manager configuration:

```
config.home.file.".config/lsd/config.yaml".text = ''
  color:
    theme: custom
'';
config.home.file.".config/lsd/colors.yaml".text = builtins.readFile (config.scheme {
  templateRepo = inputs.base16-lsd;
});
```
