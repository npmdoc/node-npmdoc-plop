# api documentation for  [plop (v1.7.4)](https://github.com/amwmedia/plop)  [![npm package](https://img.shields.io/npm/v/npmdoc-plop.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-plop) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-plop.svg)](https://travis-ci.org/npmdoc/node-npmdoc-plop)
#### Micro-generator framework that makes it easy for an entire team to create files with a level of uniformity

[![NPM](https://nodei.co/npm/plop.png?downloads=true)](https://www.npmjs.com/package/plop)

[![apidoc](https://npmdoc.github.io/node-npmdoc-plop/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-plop_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-plop/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-plop/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-plop/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Andrew Worcester",
        "email": "andrew@amwmedia.com",
        "url": "http://amwmedia.com"
    },
    "bin": {
        "plop": "./src/plop.js"
    },
    "bugs": {
        "url": "https://github.com/amwmedia/plop/issues"
    },
    "dependencies": {
        "chalk": "^1.1.3",
        "interpret": "^1.0.0",
        "liftoff": "^2.2.0",
        "minimist": "^1.2.0",
        "node-plop": "~0.5.5",
        "v8flags": "^2.0.10"
    },
    "description": "Micro-generator framework that makes it easy for an entire team to create files with a level of uniformity",
    "devDependencies": {
        "inquirer-directory": "^2.1.0",
        "plop-pack-fancy-comments": "^0.2.0"
    },
    "directories": {},
    "dist": {
        "shasum": "16d73eada04bb46ad1df31d72ae600db7009fae3",
        "tarball": "https://registry.npmjs.org/plop/-/plop-1.7.4.tgz"
    },
    "engines": {
        "node": ">=4.0"
    },
    "gitHead": "b3868d722d559d47371e97eae7901810a7b78d96",
    "homepage": "https://github.com/amwmedia/plop",
    "keywords": [
        "generator",
        "scaffolding",
        "yeoman",
        "make",
        "build",
        "generate",
        "gen",
        "plop"
    ],
    "license": "MIT",
    "main": "./src/plop.js",
    "maintainers": [
        {
            "name": "amwmedia",
            "email": "andrew@amwmedia.com"
        }
    ],
    "name": "plop",
    "optionalDependencies": {},
    "preferGlobal": "true",
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/amwmedia/plop.git"
    },
    "scripts": {},
    "version": "1.7.4"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module plop](#apidoc.module.plop)
1.  object <span class="apidocSignatureSpan">plop.</span>console_out

#### [module plop.console_out](#apidoc.module.plop.console_out)
1.  [function <span class="apidocSignatureSpan">plop.console_out.</span>chooseOptionFromList (plopList)](#apidoc.element.plop.console_out.chooseOptionFromList)
1.  [function <span class="apidocSignatureSpan">plop.console_out.</span>createInitPlopfile (cwd, callback)](#apidoc.element.plop.console_out.createInitPlopfile)
1.  [function <span class="apidocSignatureSpan">plop.console_out.</span>displayHelpScreen ()](#apidoc.element.plop.console_out.displayHelpScreen)



# <a name="apidoc.module.plop"></a>[module plop](#apidoc.module.plop)



# <a name="apidoc.module.plop.console_out"></a>[module plop.console_out](#apidoc.module.plop.console_out)

#### <a name="apidoc.element.plop.console_out.chooseOptionFromList"></a>[function <span class="apidocSignatureSpan">plop.console_out.</span>chooseOptionFromList (plopList)](#apidoc.element.plop.console_out.chooseOptionFromList)
- description and source-code
```javascript
function chooseOptionFromList(plopList) {
		const plop = nodePlop();
		const generator = plop.setGenerator('choose', {
			prompts: [{
				type: 'list',
				name: 'generator',
				message: '[PLOP]'.blue + ' Please choose a generator.',
				choices: plopList.map(function (p) {
					return {
						name: p.name + chalk.gray(!!p.description ? ' - ' + p.description : ''),
						value: p.name
					};
				})
			}]
		});
		return generator.runPrompts().then(results => results.generator);
	}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.plop.console_out.createInitPlopfile"></a>[function <span class="apidocSignatureSpan">plop.console_out.</span>createInitPlopfile (cwd, callback)](#apidoc.element.plop.console_out.createInitPlopfile)
- description and source-code
```javascript
function createInitPlopfile(cwd, callback){
		var initString = 'module.exports = function (plop) {\n\n' +
			'\tplop.setGenerator(\'basics\', {\n' +
			'\t\tdescription: \'this is a skeleton plopfile\',\n' +
			'\t\tprompts: [],\n' +
			'\t\tactions: []\n' +
			'\t});\n\n' +
			'};';

		fs.writeFile(cwd + '/plopfile.js', initString, callback);
	}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.plop.console_out.displayHelpScreen"></a>[function <span class="apidocSignatureSpan">plop.console_out.</span>displayHelpScreen ()](#apidoc.element.plop.console_out.displayHelpScreen)
- description and source-code
```javascript
function displayHelpScreen() {
		console.log(
			'\n' +
			'USAGE:\n' +
			'  $ plop\t\tSelect from a list of available generators\n' +
			'  $ plop <name>\t\tRun a generator registered under that name\n' +

			'\n' +
			'OPTIONS:\n' +
			'  -h, --help\t\tShow this help display\n' +
			'  -i, --init\t\tGenerate a basic plopfile.js\n' +
			'  -v, --version\t\tPrint current version\n'
		);
	}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
