# Greg PHP View

[![StyleCI](https://styleci.io/repos/70835580/shield?style=flat)](https://styleci.io/repos/70835580)
[![Build Status](https://travis-ci.org/greg-md/php-view.svg)](https://travis-ci.org/greg-md/php-view)
[![Total Downloads](https://poser.pugx.org/greg-md/php-view/d/total.svg)](https://packagist.org/packages/greg-md/php-view)
[![Latest Stable Version](https://poser.pugx.org/greg-md/php-view/v/stable.svg)](https://packagist.org/packages/greg-md/php-view)
[![Latest Unstable Version](https://poser.pugx.org/greg-md/php-view/v/unstable.svg)](https://packagist.org/packages/greg-md/php-view)
[![License](https://poser.pugx.org/greg-md/php-view/license.svg)](https://packagist.org/packages/greg-md/php-view)

A better Viewer and Blade Compiler for web artisans.

# Documentation

## Viewer

`\Greg\View\Viewer` is the main class which initialize a new view manager.

#### Example:

```php
$viewer = new \Greg\View\Viewer('./views', $sharedParams = []);

$response = $viewer->render('home', [
    'author' => 'Greg',
]);

$response->send();
```

#### Methods:

- **`__construct(string|array $path, array $params = [])`** 

 This is the constructor of the Viewer.

 **Arguments:**

 `$path` - Templates directory;  
 `$params` - This parameters will be assigned in all templates.

 **Example:**

 ```php
 $viewer->render('home', [
     'author' => 'Greg',
 ]);
 ```

- **`render(string $name, array $params = [], boolean $returnAsString = false)`**

 Render a template by name.

 **Arguments:**

 `$name` - Template name, relative to registered paths;  
 `$params` - Template parameters. Will be available only in this template.  
 `$returnAsString` - If `true`, returned content will be a string, otherwise will return an `\Greg\Support\Http\Response` object.

- **`renderIfExists(string $name, array $params = [], boolean $returnAsString = false)`**

 Render a template by name if template exists.

 **Arguments:**

 `$name` - Template name, relative to registered paths;  
 `$params` - Template parameters. Will be available only in this template.  
 `$returnAsString` - If `true`, returned content will be a string, otherwise will return an `\Greg\Support\Http\Response` object.

- **`renderFile(string $file, array $params = [], boolean $returnAsString = false)`**

 Render a template by name if template exists.

 **Arguments:**

 `$file` - Template file path;  
 `$params` - Template parameters. Will be available only in this template.  
 `$returnAsString` - If `true`, returned content will be a string, otherwise will return an `\Greg\Support\Http\Response` object.

- **`getRenderer(string $name, array $params = [])`**

 Get an instance of `\Greg\View\ViewRenderer` by template name.

 **Arguments:**

 `$name` - Template name, relative to registered paths;  
 `$params` - Template parameters. Will be available only in this template.  

- **`getRendererIfExists(string $name, array $params = [])`**

 Get an instance of `\Greg\View\ViewRenderer` by template name if template exists.

 **Arguments:**

 `$name` - Template name, relative to registered paths;  
 `$params` - Template parameters. Will be available only in this template.  

- **`getRendererFile(string $file, array $params = [])`**

 Get an instance of `\Greg\View\ViewRenderer` by template name if template exists.

 **Arguments:**

 `$file` - Template file path;  
 `$params` - Template parameters. Will be available only in this template.  

- **`assign(string|array $key, string $value = null)`**

 Assign parameters to all templates.

 **Arguments:**

 `$key` - Parameter key or an array of parameters;  
 `$value` - Parameter value if `$key` is not an array.  

- **`setPaths(array $paths)`**

 Replace templates directories.

 **Arguments:**

 `$paths` - Templates directories.  

- **`addPaths(array $paths)`**

 Add new templates directories.

 **Arguments:**

 `$paths` - Templates directories.  

- **`addPath(string $path)`**

 Add new template directory.

 **Arguments:**

 `$path` - Template directory.  

- **`getPaths()`**

 Get templates directories.

- **`addExtension(string $extension, \Greg\View\CompilerInterface|callable $compiler = null)`**

 Add new extension.

 **Arguments:**

 `$extension` - File extension.  
 `$compiler` - File compiler.

- **`getExtensions()`**

 Get all known extensions.

- **`getCompiler(string $extension)`**

 Get compiler by extension.

 **Arguments:**

 `$extension` - File extension.

- **`getCompilers()`**

 Get all registered compilers.

- **`getCompilersExtensions()`**

 Get all extensions which have compilers.

- **`getFile(string $name)`**

 Get file path by template name.

 **Arguments:**

 `$name` - Template name.

- **`clearCompiledFiles()`**

 Clear all compiled files.

- **`directive(string $name, callable $callable)`**

 Register a new directive.

 **Arguments:**

 `$name` - Directive name;  
 `$callable` - Directive executive function.

- **`format(string $name, mixed ...$args)`**

 Register a new directive.

 **Arguments:**

 `$name` - Directive name;  
 `...$args` - Directive arguments.
