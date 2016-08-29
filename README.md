# Visual Studio Code API externs for Haxe

This extern library makes it possible to write extensions for [Visual Studio Code](https://code.visualstudio.com/)
using [Haxe](https://haxe.org/).

VS Code API version: **1.4.0**

**NOTE**: Currently requires Haxe development build (see http://build.haxe.org/).

## Usage

Global functions and variables from the `vscode` namespace are available through `Vscode` class,
while types defined in `vscode` namespace are located in the `vscode` haxe package.

VS Code expects a .js module that exports the `activate` function that will be called upon
extension activation. In Haxe this is done using the `@:expose` metdata.

Example:
```haxe
class HelloHaxe {
    @:expose("activate")
    static function activate(context:vscode.ExtensionContext) {
        Vscode.window.showInformationMessage("Hello from Haxe!");
    }
}
```

compile with:

```
haxe -lib vscode -js hellohaxe.js HelloHaxe
```
