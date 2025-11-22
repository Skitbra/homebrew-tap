# Homebrew Tap

This is a custom Homebrew tap for installing software packages.

## Usage

### Add the tap

```bash
brew tap skitbra/tap
```

### Install a formula

```bash
brew install skitbra/tap/<formula-name>
```

Or after tapping:

```bash
brew install <formula-name>
```

### Remove the tap

```bash
brew untap skitbra/tap
```

## Available Formulae

Check the `Formula/` directory for available formulae.

## Adding New Formulae

To add a new formula to this tap:

1. Create a new Ruby file in the `Formula/` directory
2. Follow the [Homebrew Formula Cookbook](https://docs.brew.sh/Formula-Cookbook) for formula structure
3. Test your formula with `brew install --build-from-source <formula-name>`
4. Commit and push your changes

## Formula Template

```ruby
class MyFormula < Formula
  desc "Description of your software"
  homepage "https://example.com"
  url "https://example.com/releases/myformula-1.0.0.tar.gz"
  sha256 "abc123..." # SHA256 checksum of the archive
  license "MIT"

  def install
    bin.install "myformula"
  end

  test do
    system "#{bin}/myformula", "--version"
  end
end
```

## Resources

- [Homebrew Documentation](https://docs.brew.sh/)
- [Formula Cookbook](https://docs.brew.sh/Formula-Cookbook)
- [Acceptable Formulae](https://docs.brew.sh/Acceptable-Formulae)
