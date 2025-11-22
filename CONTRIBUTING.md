# Contributing to this Homebrew Tap

Thank you for your interest in contributing!

## Adding a New Formula

1. **Fork and Clone**: Fork this repository and clone it locally
2. **Create Formula**: Add a new `.rb` file in the `Formula/` directory
3. **Follow Conventions**: Use the Ruby class name that matches the formula name
4. **Test Locally**: Test your formula with:
   ```bash
   brew install --build-from-source ./Formula/your-formula.rb
   brew test your-formula
   brew audit --strict your-formula
   ```
5. **Submit PR**: Create a pull request with your changes

## Formula Guidelines

### Naming
- Formula files should be lowercase with hyphens (e.g., `my-app.rb`)
- Class names should be CamelCase (e.g., `MyApp`)
- Remove common prefixes/suffixes in class names (e.g., `node-package` → `NodePackage`)

### Required Fields
```ruby
class YourFormula < Formula
  desc "Short description (max 80 chars)"
  homepage "https://your-project-homepage.com"
  url "https://github.com/user/repo/archive/v1.0.0.tar.gz"
  sha256 "abc123..." # Use `shasum -a 256 file.tar.gz`
  license "MIT" # or appropriate license
end
```

### Installation Methods

**For compiled software:**
```ruby
def install
  system "./configure", "--prefix=#{prefix}"
  system "make", "install"
end
```

**For Python packages:**
```ruby
depends_on "python@3.11"

def install
  virtualenv_install_with_resources
end
```

**For Node.js packages:**
```ruby
depends_on "node"

def install
  system "npm", "install", *std_npm_args
end
```

**For simple binaries:**
```ruby
def install
  bin.install "your-binary"
end
```

### Testing
Always include a test block:
```ruby
test do
  system "#{bin}/your-app", "--version"
end
```

## Useful Commands

```bash
# Install from local formula file
brew install --build-from-source ./Formula/your-formula.rb

# Test the formula
brew test your-formula

# Audit for issues
brew audit --strict your-formula

# Check formula style
brew style your-formula

# Uninstall for testing
brew uninstall your-formula
```

## Resources

- [Homebrew Formula Cookbook](https://docs.brew.sh/Formula-Cookbook)
- [Homebrew Python Guide](https://docs.brew.sh/Python-for-Formula-Authors)
- [Homebrew Node Guide](https://docs.brew.sh/Node-for-Formula-Authors)
- [Formula API Documentation](https://rubydoc.brew.sh/Formula)
