# Editor configuration, see https://editorconfig.org
root = true

[*]
charset = utf-8
indent_style = space
indent_size = 2
insert_final_newline = true
trim_trailing_whitespace = true

[*.ts]
quote_type = single

[*.md]
max_line_length = off
trim_trailing_whitespace = false

# See http://help.github.com/ignore-files/ for more about ignoring files.

# compiled output
/dist
/tmp
/out-tsc
# Only exists if Bazel was run
/bazel-out

# dependencies
/node_modules

# profiling files
chrome-profiler-events*.json

# IDEs and editors
/.idea
.project
.classpath
.c9/
*.launch
.settings/
*.sublime-workspace

# IDE - VSCode
.vscode/*
!.vscode/settings.json
!.vscode/tasks.json
!.vscode/launch.json
!.vscode/extensions.json
.history/*

# misc
/.angular/cache
/.sass-cache
/connect.lock
/coverage
/libpeerconnection.log
npm-debug.log
yarn-error.log
testem.log
/typings

# System Files
.DS_Store
Thumbs.db

{
  "$schema": "./node_modules/@angular/cli/lib/config/schema.json",
  "version": 1,
  "newProjectRoot": "projects",
  "projects": {
    "app": {
      "projectType": "application",
      "schematics": {
        "@schematics/angular:component": {
          "style": "scss"
        },
        "@schematics/angular:application": {
          "strict": true
        }
      },
      "root": "",
      "sourceRoot": "src",
      "prefix": "app",
      "architect": {
        "build": {
          "builder": "@angular-devkit/build-angular:browser",
          "options": {
            "outputPath": "dist/app",
            "index": "src/index.html",
            "main": "src/main.ts",
            "polyfills": "src/polyfills.ts",
            "tsConfig": "tsconfig.app.json",
            "inlineStyleLanguage": "scss",
            "assets": [
              "src/favicon.ico",
              "src/assets"
            ],
            "styles": [
              "src/styles.scss"
            ],
            "scripts": []
          },
          "configurations": {
            "production": {
              "budgets": [
                {
                  "type": "initial",
                  "maximumWarning": "500kb",
                  "maximumError": "1mb"
                },
                {
                  "type": "anyComponentStyle",
                  "maximumWarning": "2kb",
                  "maximumError": "4kb"
                }
              ],
              "fileReplacements": [
                {
                  "replace": "src/environments/environment.ts",
                  "with": "src/environments/environment.prod.ts"
                }
              ],
              "outputHashing": "all"
            },
            "development": {
              "buildOptimizer": false,
              "optimization": false,
              "vendorChunk": true,
              "extractLicenses": false,
              "sourceMap": true,
              "namedChunks": true
            }
          },
          "defaultConfiguration": "production"
        },
        "serve": {
          "builder": "@angular-devkit/build-angular:dev-server",
          "configurations": {
            "production": {
              "browserTarget": "app:build:production"
            },
            "development": {
              "browserTarget": "app:build:development"
            }
          },
          "defaultConfiguration": "development"
        },
        "extract-i18n": {
          "builder": "@angular-devkit/build-angular:extract-i18n",
          "options": {
            "browserTarget": "app:build"
          }
        },
        "test": {
          "builder": "@angular-devkit/build-angular:karma",
          "options": {
            "main": "src/test.ts",
            "polyfills": "src/polyfills.ts",
            "tsConfig": "tsconfig.spec.json",
            "karmaConfig": "karma.conf.js",
            "inlineStyleLanguage": "scss",
            "assets": [
              "src/favicon.ico",
              "src/assets"
            ],
            "styles": [
              "src/styles.scss"
            ],
            "scripts": []
          }
        }
      }
    }
  },
  "defaultProject": "app"
}

{
  "posts": [
    {
      "id": 1,
      "firstName": "Arun",
      "lastName": "pandi",
      "email": "arunpandi@gmail.com",
      "mobile": 6381541901,
      "salary": "$ 50000"
    }
  ],
  "signupUsers": [
    {
      "id": 1,
      "body": "some comment",
      "postId": 1
    },
    {
      "fullname": "Arunpandi",
      "email": "arunpandi@gmail.com",
      "password": "system@123",
      "mobile": 6381541901,
      "id": 2
    }
  ],
  "profile": {
    "name": "typicode"
  }
}
// Karma configuration file, see link for more information
// https://karma-runner.github.io/1.0/config/configuration-file.html

module.exports = function (config) {
  config.set({
    basePath: '',
    frameworks: ['jasmine', '@angular-devkit/build-angular'],
    plugins: [
      require('karma-jasmine'),
      require('karma-chrome-launcher'),
      require('karma-jasmine-html-reporter'),
      require('karma-coverage'),
      require('@angular-devkit/build-angular/plugins/karma')
    ],
    client: {
      jasmine: {
        // you can add configuration options for Jasmine here
        // the possible options are listed at https://jasmine.github.io/api/edge/Configuration.html
        // for example, you can disable the random execution with `random: false`
        // or set a specific seed with `seed: 4321`
      },
      clearContext: false // leave Jasmine Spec Runner output visible in browser
    },
    jasmineHtmlReporter: {
      suppressAll: true // removes the duplicated traces
    },
    coverageReporter: {
      dir: require('path').join(__dirname, './coverage/app'),
      subdir: '.',
      reporters: [
        { type: 'html' },
        { type: 'text-summary' }
      ]
    },
    reporters: ['progress', 'kjhtml'],
    port: 9876,
    colors: true,
    logLevel: config.LOG_INFO,
    autoWatch: true,
    browsers: ['Chrome'],
    singleRun: false,
    restartOnFileChange: true
  });
};

{
  "name": "app",
  "version": "0.0.0",
  "scripts": {
    "ng": "ng",
    "start": "ng serve",
    "build": "ng build",
    "watch": "ng build --watch --configuration development",
    "test": "ng test"
  },
  "private": true,
  "dependencies": {
    "@angular/animations": "~13.1.0",
    "@angular/common": "~13.1.0",
    "@angular/compiler": "~13.1.0",
    "@angular/core": "~13.1.0",
    "@angular/forms": "~13.1.0",
    "@angular/platform-browser": "~13.1.0",
    "@angular/platform-browser-dynamic": "~13.1.0",
    "@angular/router": "~13.1.0",
    "bootstrap": "^5.1.3",
    "json-server": "^0.17.0",
    "rxjs": "~7.4.0",
    "tslib": "^2.3.0",
    "zone.js": "~0.11.4"
  },
  "devDependencies": {
    "@angular-devkit/build-angular": "~13.1.2",
    "@angular/cli": "~13.1.2",
    "@angular/compiler-cli": "~13.1.0",
    "@types/jasmine": "~3.10.0",
    "@types/node": "^12.11.1",
    "jasmine-core": "~3.10.0",
    "karma": "~6.3.0",
    "karma-chrome-launcher": "~3.1.0",
    "karma-coverage": "~2.1.0",
    "karma-jasmine": "~4.0.0",
    "karma-jasmine-html-reporter": "~1.7.0",
    "typescript": "~4.5.2"
  }
}

{
  "name": "app",
  "version": "0.0.0",
  "lockfileVersion": 2,
  "requires": true,
  "packages": {
    "": {
      "name": "app",
      "version": "0.0.0",
      "dependencies": {
        "@angular/animations": "~13.1.0",
        "@angular/common": "~13.1.0",
        "@angular/compiler": "~13.1.0",
        "@angular/core": "~13.1.0",
        "@angular/forms": "~13.1.0",
        "@angular/platform-browser": "~13.1.0",
        "@angular/platform-browser-dynamic": "~13.1.0",
        "@angular/router": "~13.1.0",
        "bootstrap": "^5.1.3",
        "json-server": "^0.17.0",
        "rxjs": "~7.4.0",
        "tslib": "^2.3.0",
        "zone.js": "~0.11.4"
      },
      "devDependencies": {
        "@angular-devkit/build-angular": "~13.1.2",
        "@angular/cli": "~13.1.2",
        "@angular/compiler-cli": "~13.1.0",
        "@types/jasmine": "~3.10.0",
        "@types/node": "^12.11.1",
        "jasmine-core": "~3.10.0",
        "karma": "~6.3.0",
        "karma-chrome-launcher": "~3.1.0",
        "karma-coverage": "~2.1.0",
        "karma-jasmine": "~4.0.0",
        "karma-jasmine-html-reporter": "~1.7.0",
        "typescript": "~4.5.2"
      }
    },
    "node_modules/@ampproject/remapping": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/@ampproject/remapping/-/remapping-1.0.2.tgz",
      "integrity": "sha512-SncaVxs+E3EdoA9xJgHfWPxZfowAgeIsd71VpqCKP6KNKm6s7zSqqvUc70UpKUFsrV3dAmy6qxHoIj5NG+3DiA==",
      "dev": true,
      "dependencies": {
        "@jridgewell/resolve-uri": "1.0.0",
        "sourcemap-codec": "1.4.8"
      },
      "engines": {
        "node": ">=6.0.0"
      }
    },
    "node_modules/@angular-devkit/architect": {
      "version": "0.1301.4",
      "resolved": "https://registry.npmjs.org/@angular-devkit/architect/-/architect-0.1301.4.tgz",
      "integrity": "sha512-p6G8CEMnE+gYwxRyEttj3QGsuNJ3Kusi7iwBIzWyf2RpJSdGzXdwUEiRGg6iS0YHFr06/ZFfAWfnM2DQvNm4TA==",
      "dev": true,
      "dependencies": {
        "@angular-devkit/core": "13.1.4",
        "rxjs": "6.6.7"
      },
      "engines": {
        "node": "^12.20.0 || ^14.15.0 || >=16.10.0",
        "npm": "^6.11.0 || ^7.5.6 || >=8.0.0",
        "yarn": ">= 1.13.0"
      }
    },
    "node_modules/@angular-devkit/architect/node_modules/rxjs": {
      "version": "6.6.7",
      "resolved": "https://registry.npmjs.org/rxjs/-/rxjs-6.6.7.tgz",
      "integrity": "sha512-hTdwr+7yYNIT5n4AMYp85KA6yw2Va0FLa3Rguvbpa4W3I5xynaBZo41cM3XM+4Q6fRMj3sBYIR1VAmZMXYJvRQ==",
      "dev": true,
      "dependencies": {
        "tslib": "^1.9.0"
      },
      "engines": {
        "npm": ">=2.0.0"
      }
    },
    "node_modules/@angular-devkit/architect/node_modules/tslib": {
      "version": "1.14.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-1.14.1.tgz",
      "integrity": "sha512-Xni35NKzjgMrwevysHTCArtLDpPvye8zV/0E4EyYn43P7/7qvQwPh9BGkHewbMulVntbigmcT7rdX3BNo9wRJg==",
      "dev": true
    },
    "node_modules/@angular-devkit/build-angular": {
      "version": "13.1.4",
      "resolved": "https://registry.npmjs.org/@angular-devkit/build-angular/-/build-angular-13.1.4.tgz",
      "integrity": "sha512-MTvlUCb02J4ODXDsnit4N0PR9PkpKeSYpTPueaSBuWTBeP3dvMPZQabvb3C5QT/5yUzBiXQZq11QYx3Gui4StA==",
      "dev": true,
      "dependencies": {
        "@ampproject/remapping": "1.0.2",
        "@angular-devkit/architect": "0.1301.4",
        "@angular-devkit/build-webpack": "0.1301.4",
        "@angular-devkit/core": "13.1.4",
        "@babel/core": "7.16.0",
        "@babel/generator": "7.16.0",
        "@babel/helper-annotate-as-pure": "7.16.0",
        "@babel/plugin-proposal-async-generator-functions": "7.16.4",
        "@babel/plugin-transform-async-to-generator": "7.16.0",
        "@babel/plugin-transform-runtime": "7.16.4",
        "@babel/preset-env": "7.16.4",
        "@babel/runtime": "7.16.3",
        "@babel/template": "7.16.0",
        "@discoveryjs/json-ext": "0.5.6",
        "@ngtools/webpack": "13.1.4",
        "ansi-colors": "4.1.1",
        "babel-loader": "8.2.3",
        "babel-plugin-istanbul": "6.1.1",
        "browserslist": "^4.9.1",
        "cacache": "15.3.0",
        "circular-dependency-plugin": "5.2.2",
        "copy-webpack-plugin": "10.0.0",
        "core-js": "3.19.3",
        "critters": "0.0.16",
        "css-loader": "6.5.1",
        "esbuild-wasm": "0.14.11",
        "glob": "7.2.0",
        "https-proxy-agent": "5.0.0",
        "inquirer": "8.2.0",
        "jsonc-parser": "3.0.0",
        "karma-source-map-support": "1.4.0",
        "less": "4.1.2",
        "less-loader": "10.2.0",
        "license-webpack-plugin": "4.0.0",
        "loader-utils": "3.2.0",
        "mini-css-extract-plugin": "2.4.5",
        "minimatch": "3.0.4",
        "open": "8.4.0",
        "ora": "5.4.1",
        "parse5-html-rewriting-stream": "6.0.1",
        "piscina": "3.1.0",
        "postcss": "8.4.4",
        "postcss-import": "14.0.2",
        "postcss-loader": "6.2.1",
        "postcss-preset-env": "7.2.3",
        "regenerator-runtime": "0.13.9",
        "resolve-url-loader": "4.0.0",
        "rxjs": "6.6.7",
        "sass": "1.44.0",
        "sass-loader": "12.4.0",
        "semver": "7.3.5",
        "source-map-loader": "3.0.0",
        "source-map-support": "0.5.21",
        "stylus": "0.55.0",
        "stylus-loader": "6.2.0",
        "terser": "5.10.0",
        "text-table": "0.2.0",
        "tree-kill": "1.2.2",
        "tslib": "2.3.1",
        "webpack": "5.65.0",
        "webpack-dev-middleware": "5.2.2",
        "webpack-dev-server": "4.6.0",
        "webpack-merge": "5.8.0",
        "webpack-subresource-integrity": "5.0.0"
      },
      "engines": {
        "node": "^12.20.0 || ^14.15.0 || >=16.10.0",
        "npm": "^6.11.0 || ^7.5.6 || >=8.0.0",
        "yarn": ">= 1.13.0"
      },
      "optionalDependencies": {
        "esbuild": "0.14.11"
      },
      "peerDependencies": {
        "@angular/compiler-cli": "^13.0.0 || ^13.1.0-next",
        "@angular/localize": "^13.0.0 || ^13.1.0-next",
        "@angular/service-worker": "^13.0.0 || ^13.1.0-next",
        "karma": "^6.3.0",
        "ng-packagr": "^13.0.0 || ^13.1.0-next",
        "protractor": "^7.0.0",
        "tailwindcss": "^2.0.0 || ^3.0.0",
        "typescript": ">=4.4.3 <4.6"
      },
      "peerDependenciesMeta": {
        "@angular/localize": {
          "optional": true
        },
        "@angular/service-worker": {
          "optional": true
        },
        "karma": {
          "optional": true
        },
        "ng-packagr": {
          "optional": true
        },
        "protractor": {
          "optional": true
        },
        "tailwindcss": {
          "optional": true
        }
      }
    },
    "node_modules/@angular-devkit/build-angular/node_modules/rxjs": {
      "version": "6.6.7",
      "resolved": "https://registry.npmjs.org/rxjs/-/rxjs-6.6.7.tgz",
      "integrity": "sha512-hTdwr+7yYNIT5n4AMYp85KA6yw2Va0FLa3Rguvbpa4W3I5xynaBZo41cM3XM+4Q6fRMj3sBYIR1VAmZMXYJvRQ==",
      "dev": true,
      "dependencies": {
        "tslib": "^1.9.0"
      },
      "engines": {
        "npm": ">=2.0.0"
      }
    },
    "node_modules/@angular-devkit/build-angular/node_modules/rxjs/node_modules/tslib": {
      "version": "1.14.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-1.14.1.tgz",
      "integrity": "sha512-Xni35NKzjgMrwevysHTCArtLDpPvye8zV/0E4EyYn43P7/7qvQwPh9BGkHewbMulVntbigmcT7rdX3BNo9wRJg==",
      "dev": true
    },
    "node_modules/@angular-devkit/build-webpack": {
      "version": "0.1301.4",
      "resolved": "https://registry.npmjs.org/@angular-devkit/build-webpack/-/build-webpack-0.1301.4.tgz",
      "integrity": "sha512-IcC3Y5WhreIV0uT90ITqJVgRqFjGwH72hftwLxkslaX+FJDcL36mhsNdyN66BJiuX7R85xUxHq3PEb9cZrllJA==",
      "dev": true,
      "dependencies": {
        "@angular-devkit/architect": "0.1301.4",
        "rxjs": "6.6.7"
      },
      "engines": {
        "node": "^12.20.0 || ^14.15.0 || >=16.10.0",
        "npm": "^6.11.0 || ^7.5.6 || >=8.0.0",
        "yarn": ">= 1.13.0"
      },
      "peerDependencies": {
        "webpack": "^5.30.0",
        "webpack-dev-server": "^4.0.0"
      }
    },
    "node_modules/@angular-devkit/build-webpack/node_modules/rxjs": {
      "version": "6.6.7",
      "resolved": "https://registry.npmjs.org/rxjs/-/rxjs-6.6.7.tgz",
      "integrity": "sha512-hTdwr+7yYNIT5n4AMYp85KA6yw2Va0FLa3Rguvbpa4W3I5xynaBZo41cM3XM+4Q6fRMj3sBYIR1VAmZMXYJvRQ==",
      "dev": true,
      "dependencies": {
        "tslib": "^1.9.0"
      },
      "engines": {
        "npm": ">=2.0.0"
      }
    },
    "node_modules/@angular-devkit/build-webpack/node_modules/tslib": {
      "version": "1.14.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-1.14.1.tgz",
      "integrity": "sha512-Xni35NKzjgMrwevysHTCArtLDpPvye8zV/0E4EyYn43P7/7qvQwPh9BGkHewbMulVntbigmcT7rdX3BNo9wRJg==",
      "dev": true
    },
    "node_modules/@angular-devkit/core": {
      "version": "13.1.4",
      "resolved": "https://registry.npmjs.org/@angular-devkit/core/-/core-13.1.4.tgz",
      "integrity": "sha512-225Gjy4iVxh5Jo9njJnaG75M/Dt95UW+dEPCGWKV5E/++7UUlXlo9sNWq8x2vJm2nhtsPkpnXNOt4pW1mIDwqQ==",
      "dev": true,
      "dependencies": {
        "ajv": "8.8.2",
        "ajv-formats": "2.1.1",
        "fast-json-stable-stringify": "2.1.0",
        "magic-string": "0.25.7",
        "rxjs": "6.6.7",
        "source-map": "0.7.3"
      },
      "engines": {
        "node": "^12.20.0 || ^14.15.0 || >=16.10.0",
        "npm": "^6.11.0 || ^7.5.6 || >=8.0.0",
        "yarn": ">= 1.13.0"
      },
      "peerDependencies": {
        "chokidar": "^3.5.2"
      },
      "peerDependenciesMeta": {
        "chokidar": {
          "optional": true
        }
      }
    },
    "node_modules/@angular-devkit/core/node_modules/rxjs": {
      "version": "6.6.7",
      "resolved": "https://registry.npmjs.org/rxjs/-/rxjs-6.6.7.tgz",
      "integrity": "sha512-hTdwr+7yYNIT5n4AMYp85KA6yw2Va0FLa3Rguvbpa4W3I5xynaBZo41cM3XM+4Q6fRMj3sBYIR1VAmZMXYJvRQ==",
      "dev": true,
      "dependencies": {
        "tslib": "^1.9.0"
      },
      "engines": {
        "npm": ">=2.0.0"
      }
    },
    "node_modules/@angular-devkit/core/node_modules/tslib": {
      "version": "1.14.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-1.14.1.tgz",
      "integrity": "sha512-Xni35NKzjgMrwevysHTCArtLDpPvye8zV/0E4EyYn43P7/7qvQwPh9BGkHewbMulVntbigmcT7rdX3BNo9wRJg==",
      "dev": true
    },
    "node_modules/@angular-devkit/schematics": {
      "version": "13.1.4",
      "resolved": "https://registry.npmjs.org/@angular-devkit/schematics/-/schematics-13.1.4.tgz",
      "integrity": "sha512-yBa7IeC4cLZ7s137NAQD+sMB5c6SI6UJ6xYxl6J/CvV2RLGOZZA93i4GuRALi5s82eLi1fH+HEL/gvf3JQynzQ==",
      "dev": true,
      "dependencies": {
        "@angular-devkit/core": "13.1.4",
        "jsonc-parser": "3.0.0",
        "magic-string": "0.25.7",
        "ora": "5.4.1",
        "rxjs": "6.6.7"
      },
      "engines": {
        "node": "^12.20.0 || ^14.15.0 || >=16.10.0",
        "npm": "^6.11.0 || ^7.5.6 || >=8.0.0",
        "yarn": ">= 1.13.0"
      }
    },
    "node_modules/@angular-devkit/schematics/node_modules/rxjs": {
      "version": "6.6.7",
      "resolved": "https://registry.npmjs.org/rxjs/-/rxjs-6.6.7.tgz",
      "integrity": "sha512-hTdwr+7yYNIT5n4AMYp85KA6yw2Va0FLa3Rguvbpa4W3I5xynaBZo41cM3XM+4Q6fRMj3sBYIR1VAmZMXYJvRQ==",
      "dev": true,
      "dependencies": {
        "tslib": "^1.9.0"
      },
      "engines": {
        "npm": ">=2.0.0"
      }
    },
    "node_modules/@angular-devkit/schematics/node_modules/tslib": {
      "version": "1.14.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-1.14.1.tgz",
      "integrity": "sha512-Xni35NKzjgMrwevysHTCArtLDpPvye8zV/0E4EyYn43P7/7qvQwPh9BGkHewbMulVntbigmcT7rdX3BNo9wRJg==",
      "dev": true
    },
    "node_modules/@angular/animations": {
      "version": "13.1.3",
      "resolved": "https://registry.npmjs.org/@angular/animations/-/animations-13.1.3.tgz",
      "integrity": "sha512-OwsVQsNHubIgRcxnjti4CU3QJnqd7Z2b+2iu3M349Oxyqxz4DNCqKXalDuJZt/b0yNfirvYO3kCgBfj4PF43QQ==",
      "dependencies": {
        "tslib": "^2.3.0"
      },
      "engines": {
        "node": "^12.20.0 || ^14.15.0 || >=16.10.0"
      },
      "peerDependencies": {
        "@angular/core": "13.1.3"
      }
    },
    "node_modules/@angular/cli": {
      "version": "13.1.4",
      "resolved": "https://registry.npmjs.org/@angular/cli/-/cli-13.1.4.tgz",
      "integrity": "sha512-PP9xpvDDCHhLTIZjewQQzzf+JbpF2s5mXTW2AgIL/E53ukaVvXwwjFMt9dQvECwut/LDpThoc3OfqcGrmwtqnA==",
      "dev": true,
      "hasInstallScript": true,
      "dependencies": {
        "@angular-devkit/architect": "0.1301.4",
        "@angular-devkit/core": "13.1.4",
        "@angular-devkit/schematics": "13.1.4",
        "@schematics/angular": "13.1.4",
        "@yarnpkg/lockfile": "1.1.0",
        "ansi-colors": "4.1.1",
        "debug": "4.3.3",
        "ini": "2.0.0",
        "inquirer": "8.2.0",
        "jsonc-parser": "3.0.0",
        "npm-package-arg": "8.1.5",
        "npm-pick-manifest": "6.1.1",
        "open": "8.4.0",
        "ora": "5.4.1",
        "pacote": "12.0.2",
        "resolve": "1.20.0",
        "semver": "7.3.5",
        "symbol-observable": "4.0.0",
        "uuid": "8.3.2"
      },
      "bin": {
        "ng": "bin/ng.js"
      },
      "engines": {
        "node": "^12.20.0 || ^14.15.0 || >=16.10.0",
        "npm": "^6.11.0 || ^7.5.6 || >=8.0.0",
        "yarn": ">= 1.13.0"
      }
    },
    "node_modules/@angular/common": {
      "version": "13.1.3",
      "resolved": "https://registry.npmjs.org/@angular/common/-/common-13.1.3.tgz",
      "integrity": "sha512-8qf5syeXUogf3+GSu6IRJjrk46UKh9L0QuLx+OSIl/df0y1ewx7e28q3BAUEEnOnKrLzpPNxWs2iwModc4KYfg==",
      "dependencies": {
        "tslib": "^2.3.0"
      },
      "engines": {
        "node": "^12.20.0 || ^14.15.0 || >=16.10.0"
      },
      "peerDependencies": {
        "@angular/core": "13.1.3",
        "rxjs": "^6.5.3 || ^7.4.0"
      }
    },
    "node_modules/@angular/compiler": {
      "version": "13.1.3",
      "resolved": "https://registry.npmjs.org/@angular/compiler/-/compiler-13.1.3.tgz",
      "integrity": "sha512-dbHs/Oa+Dn+7i0jKtlVDE0lD0DaUC+lVzAcTK/zS37LrckrTMn1CA+z9bZ4gpHig9RU0wgV3YORxv0wokyiB8A==",
      "dependencies": {
        "tslib": "^2.3.0"
      },
      "engines": {
        "node": "^12.20.0 || ^14.15.0 || >=16.10.0"
      }
    },
    "node_modules/@angular/compiler-cli": {
      "version": "13.1.3",
      "resolved": "https://registry.npmjs.org/@angular/compiler-cli/-/compiler-cli-13.1.3.tgz",
      "integrity": "sha512-ALURaJATc54DzPuiZBvALf/alEp1wr7Hjmw4FuMn2cU7p8lwKkra1Dz5dAZOxh7jAcD1GJfrK/+Sb7A3cuuKjQ==",
      "dev": true,
      "dependencies": {
        "@babel/core": "^7.8.6",
        "canonical-path": "1.0.0",
        "chokidar": "^3.0.0",
        "convert-source-map": "^1.5.1",
        "dependency-graph": "^0.11.0",
        "magic-string": "^0.25.0",
        "reflect-metadata": "^0.1.2",
        "semver": "^7.0.0",
        "sourcemap-codec": "^1.4.8",
        "tslib": "^2.3.0",
        "yargs": "^17.2.1"
      },
      "bin": {
        "ng-xi18n": "bundles/src/bin/ng_xi18n.js",
        "ngc": "bundles/src/bin/ngc.js",
        "ngcc": "bundles/ngcc/main-ngcc.js"
      },
      "engines": {
        "node": "^12.20.0 || ^14.15.0 || >=16.10.0"
      },
      "peerDependencies": {
        "@angular/compiler": "13.1.3",
        "typescript": ">=4.4.2 <4.6"
      }
    },
    "node_modules/@angular/core": {
      "version": "13.1.3",
      "resolved": "https://registry.npmjs.org/@angular/core/-/core-13.1.3.tgz",
      "integrity": "sha512-rvCnIAonRx7VnH2Mv9lQR+UYdlFQQetZCjPw8QOswOspEpHpEPDrp1HxDIqJnHxNqW0n8J3Zev/VgQYr0481UA==",
      "dependencies": {
        "tslib": "^2.3.0"
      },
      "engines": {
        "node": "^12.20.0 || ^14.15.0 || >=16.10.0"
      },
      "peerDependencies": {
        "rxjs": "^6.5.3 || ^7.4.0",
        "zone.js": "~0.11.4"
      }
    },
    "node_modules/@angular/forms": {
      "version": "13.1.3",
      "resolved": "https://registry.npmjs.org/@angular/forms/-/forms-13.1.3.tgz",
      "integrity": "sha512-c4N9zZSILyEbomY2CJo1WAMxiHu/qlycvzxKH5NFS2P2+fieORlbKUJ2p1CbYqcIxVnLYRSdWH8f1JpoaG0ETw==",
      "dependencies": {
        "tslib": "^2.3.0"
      },
      "engines": {
        "node": "^12.20.0 || ^14.15.0 || >=16.10.0"
      },
      "peerDependencies": {
        "@angular/common": "13.1.3",
        "@angular/core": "13.1.3",
        "@angular/platform-browser": "13.1.3",
        "rxjs": "^6.5.3 || ^7.4.0"
      }
    },
    "node_modules/@angular/platform-browser": {
      "version": "13.1.3",
      "resolved": "https://registry.npmjs.org/@angular/platform-browser/-/platform-browser-13.1.3.tgz",
      "integrity": "sha512-mnWjdr9UTNZvGk8jPI6O9FIhun8Q/0ghy3dg3I9AfRzEG4vPiIZW1ICksTiB+jV9etzhKpidtmg71bwgeXax1A==",
      "dependencies": {
        "tslib": "^2.3.0"
      },
      "engines": {
        "node": "^12.20.0 || ^14.15.0 || >=16.10.0"
      },
      "peerDependencies": {
        "@angular/animations": "13.1.3",
        "@angular/common": "13.1.3",
        "@angular/core": "13.1.3"
      },
      "peerDependenciesMeta": {
        "@angular/animations": {
          "optional": true
        }
      }
    },
    "node_modules/@angular/platform-browser-dynamic": {
      "version": "13.1.3",
      "resolved": "https://registry.npmjs.org/@angular/platform-browser-dynamic/-/platform-browser-dynamic-13.1.3.tgz",
      "integrity": "sha512-vEWyJ+2gkwh2N6KOJfxUNSdSO51ROlzCqqzCfHrPYQrlOFUfKsYKA1uoiB5UGfFEU0HBtIRWn6xoUy3wzVOZbw==",
      "dependencies": {
        "tslib": "^2.3.0"
      },
      "engines": {
        "node": "^12.20.0 || ^14.15.0 || >=16.10.0"
      },
      "peerDependencies": {
        "@angular/common": "13.1.3",
        "@angular/compiler": "13.1.3",
        "@angular/core": "13.1.3",
        "@angular/platform-browser": "13.1.3"
      }
    },
    "node_modules/@angular/router": {
      "version": "13.1.3",
      "resolved": "https://registry.npmjs.org/@angular/router/-/router-13.1.3.tgz",
      "integrity": "sha512-L86kARlc5UNi5KeI0O8PO7wFbTzjEI8ouz+z+aNmCnMUUNX0rbvbuXiPdDvLc71nKZznsPCl2IuO8ojyHrSPsQ==",
      "dependencies": {
        "tslib": "^2.3.0"
      },
      "engines": {
        "node": "^12.20.0 || ^14.15.0 || >=16.10.0"
      },
      "peerDependencies": {
        "@angular/common": "13.1.3",
        "@angular/core": "13.1.3",
        "@angular/platform-browser": "13.1.3",
        "rxjs": "^6.5.3 || ^7.4.0"
      }
    },
    "node_modules/@assemblyscript/loader": {
      "version": "0.10.1",
      "resolved": "https://registry.npmjs.org/@assemblyscript/loader/-/loader-0.10.1.tgz",
      "integrity": "sha512-H71nDOOL8Y7kWRLqf6Sums+01Q5msqBW2KhDUTemh1tvY04eSkSXrK0uj/4mmY0Xr16/3zyZmsrxN7CKuRbNRg==",
      "dev": true
    },
    "node_modules/@babel/code-frame": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/code-frame/-/code-frame-7.16.7.tgz",
      "integrity": "sha512-iAXqUn8IIeBTNd72xsFlgaXHkMBMt6y4HJp1tIaK465CWLT/fG1aqB7ykr95gHHmlBdGbFeWWfyB4NJJ0nmeIg==",
      "dev": true,
      "dependencies": {
        "@babel/highlight": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/compat-data": {
      "version": "7.16.8",
      "resolved": "https://registry.npmjs.org/@babel/compat-data/-/compat-data-7.16.8.tgz",
      "integrity": "sha512-m7OkX0IdKLKPpBlJtF561YJal5y/jyI5fNfWbPxh2D/nbzzGI4qRyrD8xO2jB24u7l+5I2a43scCG2IrfjC50Q==",
      "dev": true,
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/core": {
      "version": "7.16.0",
      "resolved": "https://registry.npmjs.org/@babel/core/-/core-7.16.0.tgz",
      "integrity": "sha512-mYZEvshBRHGsIAiyH5PzCFTCfbWfoYbO/jcSdXQSUQu1/pW0xDZAUP7KEc32heqWTAfAHhV9j1vH8Sav7l+JNQ==",
      "dev": true,
      "dependencies": {
        "@babel/code-frame": "^7.16.0",
        "@babel/generator": "^7.16.0",
        "@babel/helper-compilation-targets": "^7.16.0",
        "@babel/helper-module-transforms": "^7.16.0",
        "@babel/helpers": "^7.16.0",
        "@babel/parser": "^7.16.0",
        "@babel/template": "^7.16.0",
        "@babel/traverse": "^7.16.0",
        "@babel/types": "^7.16.0",
        "convert-source-map": "^1.7.0",
        "debug": "^4.1.0",
        "gensync": "^1.0.0-beta.2",
        "json5": "^2.1.2",
        "semver": "^6.3.0",
        "source-map": "^0.5.0"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/babel"
      }
    },
    "node_modules/@babel/core/node_modules/semver": {
      "version": "6.3.0",
      "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.0.tgz",
      "integrity": "sha512-b39TBaTSfV6yBrapU89p5fKekE2m/NwnDocOVruQFS1/veMgdzuPcnOM34M6CwxW8jH/lxEa5rBoDeUwu5HHTw==",
      "dev": true,
      "bin": {
        "semver": "bin/semver.js"
      }
    },
    "node_modules/@babel/core/node_modules/source-map": {
      "version": "0.5.7",
      "resolved": "https://registry.npmjs.org/source-map/-/source-map-0.5.7.tgz",
      "integrity": "sha1-igOdLRAh0i0eoUyA2OpGi6LvP8w=",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/@babel/generator": {
      "version": "7.16.0",
      "resolved": "https://registry.npmjs.org/@babel/generator/-/generator-7.16.0.tgz",
      "integrity": "sha512-RR8hUCfRQn9j9RPKEVXo9LiwoxLPYn6hNZlvUOR8tSnaxlD0p0+la00ZP9/SnRt6HchKr+X0fO2r8vrETiJGew==",
      "dev": true,
      "dependencies": {
        "@babel/types": "^7.16.0",
        "jsesc": "^2.5.1",
        "source-map": "^0.5.0"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/generator/node_modules/source-map": {
      "version": "0.5.7",
      "resolved": "https://registry.npmjs.org/source-map/-/source-map-0.5.7.tgz",
      "integrity": "sha1-igOdLRAh0i0eoUyA2OpGi6LvP8w=",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/@babel/helper-annotate-as-pure": {
      "version": "7.16.0",
      "resolved": "https://registry.npmjs.org/@babel/helper-annotate-as-pure/-/helper-annotate-as-pure-7.16.0.tgz",
      "integrity": "sha512-ItmYF9vR4zA8cByDocY05o0LGUkp1zhbTQOH1NFyl5xXEqlTJQCEJjieriw+aFpxo16swMxUnUiKS7a/r4vtHg==",
      "dev": true,
      "dependencies": {
        "@babel/types": "^7.16.0"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-builder-binary-assignment-operator-visitor": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-builder-binary-assignment-operator-visitor/-/helper-builder-binary-assignment-operator-visitor-7.16.7.tgz",
      "integrity": "sha512-C6FdbRaxYjwVu/geKW4ZeQ0Q31AftgRcdSnZ5/jsH6BzCJbtvXvhpfkbkThYSuutZA7nCXpPR6AD9zd1dprMkA==",
      "dev": true,
      "dependencies": {
        "@babel/helper-explode-assignable-expression": "^7.16.7",
        "@babel/types": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-compilation-targets": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-compilation-targets/-/helper-compilation-targets-7.16.7.tgz",
      "integrity": "sha512-mGojBwIWcwGD6rfqgRXVlVYmPAv7eOpIemUG3dGnDdCY4Pae70ROij3XmfrH6Fa1h1aiDylpglbZyktfzyo/hA==",
      "dev": true,
      "dependencies": {
        "@babel/compat-data": "^7.16.4",
        "@babel/helper-validator-option": "^7.16.7",
        "browserslist": "^4.17.5",
        "semver": "^6.3.0"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0"
      }
    },
    "node_modules/@babel/helper-compilation-targets/node_modules/semver": {
      "version": "6.3.0",
      "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.0.tgz",
      "integrity": "sha512-b39TBaTSfV6yBrapU89p5fKekE2m/NwnDocOVruQFS1/veMgdzuPcnOM34M6CwxW8jH/lxEa5rBoDeUwu5HHTw==",
      "dev": true,
      "bin": {
        "semver": "bin/semver.js"
      }
    },
    "node_modules/@babel/helper-create-class-features-plugin": {
      "version": "7.16.10",
      "resolved": "https://registry.npmjs.org/@babel/helper-create-class-features-plugin/-/helper-create-class-features-plugin-7.16.10.tgz",
      "integrity": "sha512-wDeej0pu3WN/ffTxMNCPW5UCiOav8IcLRxSIyp/9+IF2xJUM9h/OYjg0IJLHaL6F8oU8kqMz9nc1vryXhMsgXg==",
      "dev": true,
      "dependencies": {
        "@babel/helper-annotate-as-pure": "^7.16.7",
        "@babel/helper-environment-visitor": "^7.16.7",
        "@babel/helper-function-name": "^7.16.7",
        "@babel/helper-member-expression-to-functions": "^7.16.7",
        "@babel/helper-optimise-call-expression": "^7.16.7",
        "@babel/helper-replace-supers": "^7.16.7",
        "@babel/helper-split-export-declaration": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0"
      }
    },
    "node_modules/@babel/helper-create-class-features-plugin/node_modules/@babel/helper-annotate-as-pure": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-annotate-as-pure/-/helper-annotate-as-pure-7.16.7.tgz",
      "integrity": "sha512-s6t2w/IPQVTAET1HitoowRGXooX8mCgtuP5195wD/QJPV6wYjpujCGF7JuMODVX2ZAJOf1GT6DT9MHEZvLOFSw==",
      "dev": true,
      "dependencies": {
        "@babel/types": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-create-regexp-features-plugin": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-create-regexp-features-plugin/-/helper-create-regexp-features-plugin-7.16.7.tgz",
      "integrity": "sha512-fk5A6ymfp+O5+p2yCkXAu5Kyj6v0xh0RBeNcAkYUMDvvAAoxvSKXn+Jb37t/yWFiQVDFK1ELpUTD8/aLhCPu+g==",
      "dev": true,
      "dependencies": {
        "@babel/helper-annotate-as-pure": "^7.16.7",
        "regexpu-core": "^4.7.1"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0"
      }
    },
    "node_modules/@babel/helper-create-regexp-features-plugin/node_modules/@babel/helper-annotate-as-pure": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-annotate-as-pure/-/helper-annotate-as-pure-7.16.7.tgz",
      "integrity": "sha512-s6t2w/IPQVTAET1HitoowRGXooX8mCgtuP5195wD/QJPV6wYjpujCGF7JuMODVX2ZAJOf1GT6DT9MHEZvLOFSw==",
      "dev": true,
      "dependencies": {
        "@babel/types": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-define-polyfill-provider": {
      "version": "0.3.1",
      "resolved": "https://registry.npmjs.org/@babel/helper-define-polyfill-provider/-/helper-define-polyfill-provider-0.3.1.tgz",
      "integrity": "sha512-J9hGMpJQmtWmj46B3kBHmL38UhJGhYX7eqkcq+2gsstyYt341HmPeWspihX43yVRA0mS+8GGk2Gckc7bY/HCmA==",
      "dev": true,
      "dependencies": {
        "@babel/helper-compilation-targets": "^7.13.0",
        "@babel/helper-module-imports": "^7.12.13",
        "@babel/helper-plugin-utils": "^7.13.0",
        "@babel/traverse": "^7.13.0",
        "debug": "^4.1.1",
        "lodash.debounce": "^4.0.8",
        "resolve": "^1.14.2",
        "semver": "^6.1.2"
      },
      "peerDependencies": {
        "@babel/core": "^7.4.0-0"
      }
    },
    "node_modules/@babel/helper-define-polyfill-provider/node_modules/semver": {
      "version": "6.3.0",
      "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.0.tgz",
      "integrity": "sha512-b39TBaTSfV6yBrapU89p5fKekE2m/NwnDocOVruQFS1/veMgdzuPcnOM34M6CwxW8jH/lxEa5rBoDeUwu5HHTw==",
      "dev": true,
      "bin": {
        "semver": "bin/semver.js"
      }
    },
    "node_modules/@babel/helper-environment-visitor": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-environment-visitor/-/helper-environment-visitor-7.16.7.tgz",
      "integrity": "sha512-SLLb0AAn6PkUeAfKJCCOl9e1R53pQlGAfc4y4XuMRZfqeMYLE0dM1LMhqbGAlGQY0lfw5/ohoYWAe9V1yibRag==",
      "dev": true,
      "dependencies": {
        "@babel/types": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-explode-assignable-expression": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-explode-assignable-expression/-/helper-explode-assignable-expression-7.16.7.tgz",
      "integrity": "sha512-KyUenhWMC8VrxzkGP0Jizjo4/Zx+1nNZhgocs+gLzyZyB8SHidhoq9KK/8Ato4anhwsivfkBLftky7gvzbZMtQ==",
      "dev": true,
      "dependencies": {
        "@babel/types": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-function-name": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-function-name/-/helper-function-name-7.16.7.tgz",
      "integrity": "sha512-QfDfEnIUyyBSR3HtrtGECuZ6DAyCkYFp7GHl75vFtTnn6pjKeK0T1DB5lLkFvBea8MdaiUABx3osbgLyInoejA==",
      "dev": true,
      "dependencies": {
        "@babel/helper-get-function-arity": "^7.16.7",
        "@babel/template": "^7.16.7",
        "@babel/types": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-function-name/node_modules/@babel/template": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/template/-/template-7.16.7.tgz",
      "integrity": "sha512-I8j/x8kHUrbYRTUxXrrMbfCa7jxkE7tZre39x3kjr9hvI82cK1FfqLygotcWN5kdPGWcLdWMHpSBavse5tWw3w==",
      "dev": true,
      "dependencies": {
        "@babel/code-frame": "^7.16.7",
        "@babel/parser": "^7.16.7",
        "@babel/types": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-get-function-arity": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-get-function-arity/-/helper-get-function-arity-7.16.7.tgz",
      "integrity": "sha512-flc+RLSOBXzNzVhcLu6ujeHUrD6tANAOU5ojrRx/as+tbzf8+stUCj7+IfRRoAbEZqj/ahXEMsjhOhgeZsrnTw==",
      "dev": true,
      "dependencies": {
        "@babel/types": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-hoist-variables": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-hoist-variables/-/helper-hoist-variables-7.16.7.tgz",
      "integrity": "sha512-m04d/0Op34H5v7pbZw6pSKP7weA6lsMvfiIAMeIvkY/R4xQtBSMFEigu9QTZ2qB/9l22vsxtM8a+Q8CzD255fg==",
      "dev": true,
      "dependencies": {
        "@babel/types": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-member-expression-to-functions": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-member-expression-to-functions/-/helper-member-expression-to-functions-7.16.7.tgz",
      "integrity": "sha512-VtJ/65tYiU/6AbMTDwyoXGPKHgTsfRarivm+YbB5uAzKUyuPjgZSgAFeG87FCigc7KNHu2Pegh1XIT3lXjvz3Q==",
      "dev": true,
      "dependencies": {
        "@babel/types": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-module-imports": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-module-imports/-/helper-module-imports-7.16.7.tgz",
      "integrity": "sha512-LVtS6TqjJHFc+nYeITRo6VLXve70xmq7wPhWTqDJusJEgGmkAACWwMiTNrvfoQo6hEhFwAIixNkvB0jPXDL8Wg==",
      "dev": true,
      "dependencies": {
        "@babel/types": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-module-transforms": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-module-transforms/-/helper-module-transforms-7.16.7.tgz",
      "integrity": "sha512-gaqtLDxJEFCeQbYp9aLAefjhkKdjKcdh6DB7jniIGU3Pz52WAmP268zK0VgPz9hUNkMSYeH976K2/Y6yPadpng==",
      "dev": true,
      "dependencies": {
        "@babel/helper-environment-visitor": "^7.16.7",
        "@babel/helper-module-imports": "^7.16.7",
        "@babel/helper-simple-access": "^7.16.7",
        "@babel/helper-split-export-declaration": "^7.16.7",
        "@babel/helper-validator-identifier": "^7.16.7",
        "@babel/template": "^7.16.7",
        "@babel/traverse": "^7.16.7",
        "@babel/types": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-module-transforms/node_modules/@babel/template": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/template/-/template-7.16.7.tgz",
      "integrity": "sha512-I8j/x8kHUrbYRTUxXrrMbfCa7jxkE7tZre39x3kjr9hvI82cK1FfqLygotcWN5kdPGWcLdWMHpSBavse5tWw3w==",
      "dev": true,
      "dependencies": {
        "@babel/code-frame": "^7.16.7",
        "@babel/parser": "^7.16.7",
        "@babel/types": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-optimise-call-expression": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-optimise-call-expression/-/helper-optimise-call-expression-7.16.7.tgz",
      "integrity": "sha512-EtgBhg7rd/JcnpZFXpBy0ze1YRfdm7BnBX4uKMBd3ixa3RGAE002JZB66FJyNH7g0F38U05pXmA5P8cBh7z+1w==",
      "dev": true,
      "dependencies": {
        "@babel/types": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-plugin-utils": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-plugin-utils/-/helper-plugin-utils-7.16.7.tgz",
      "integrity": "sha512-Qg3Nk7ZxpgMrsox6HreY1ZNKdBq7K72tDSliA6dCl5f007jR4ne8iD5UzuNnCJH2xBf2BEEVGr+/OL6Gdp7RxA==",
      "dev": true,
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-remap-async-to-generator": {
      "version": "7.16.8",
      "resolved": "https://registry.npmjs.org/@babel/helper-remap-async-to-generator/-/helper-remap-async-to-generator-7.16.8.tgz",
      "integrity": "sha512-fm0gH7Flb8H51LqJHy3HJ3wnE1+qtYR2A99K06ahwrawLdOFsCEWjZOrYricXJHoPSudNKxrMBUPEIPxiIIvBw==",
      "dev": true,
      "dependencies": {
        "@babel/helper-annotate-as-pure": "^7.16.7",
        "@babel/helper-wrap-function": "^7.16.8",
        "@babel/types": "^7.16.8"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-remap-async-to-generator/node_modules/@babel/helper-annotate-as-pure": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-annotate-as-pure/-/helper-annotate-as-pure-7.16.7.tgz",
      "integrity": "sha512-s6t2w/IPQVTAET1HitoowRGXooX8mCgtuP5195wD/QJPV6wYjpujCGF7JuMODVX2ZAJOf1GT6DT9MHEZvLOFSw==",
      "dev": true,
      "dependencies": {
        "@babel/types": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-replace-supers": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-replace-supers/-/helper-replace-supers-7.16.7.tgz",
      "integrity": "sha512-y9vsWilTNaVnVh6xiJfABzsNpgDPKev9HnAgz6Gb1p6UUwf9NepdlsV7VXGCftJM+jqD5f7JIEubcpLjZj5dBw==",
      "dev": true,
      "dependencies": {
        "@babel/helper-environment-visitor": "^7.16.7",
        "@babel/helper-member-expression-to-functions": "^7.16.7",
        "@babel/helper-optimise-call-expression": "^7.16.7",
        "@babel/traverse": "^7.16.7",
        "@babel/types": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-simple-access": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-simple-access/-/helper-simple-access-7.16.7.tgz",
      "integrity": "sha512-ZIzHVyoeLMvXMN/vok/a4LWRy8G2v205mNP0XOuf9XRLyX5/u9CnVulUtDgUTama3lT+bf/UqucuZjqiGuTS1g==",
      "dev": true,
      "dependencies": {
        "@babel/types": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-skip-transparent-expression-wrappers": {
      "version": "7.16.0",
      "resolved": "https://registry.npmjs.org/@babel/helper-skip-transparent-expression-wrappers/-/helper-skip-transparent-expression-wrappers-7.16.0.tgz",
      "integrity": "sha512-+il1gTy0oHwUsBQZyJvukbB4vPMdcYBrFHa0Uc4AizLxbq6BOYC51Rv4tWocX9BLBDLZ4kc6qUFpQ6HRgL+3zw==",
      "dev": true,
      "dependencies": {
        "@babel/types": "^7.16.0"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-split-export-declaration": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-split-export-declaration/-/helper-split-export-declaration-7.16.7.tgz",
      "integrity": "sha512-xbWoy/PFoxSWazIToT9Sif+jJTlrMcndIsaOKvTA6u7QEo7ilkRZpjew18/W3c7nm8fXdUDXh02VXTbZ0pGDNw==",
      "dev": true,
      "dependencies": {
        "@babel/types": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-validator-identifier": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-validator-identifier/-/helper-validator-identifier-7.16.7.tgz",
      "integrity": "sha512-hsEnFemeiW4D08A5gUAZxLBTXpZ39P+a+DGDsHw1yxqyQ/jzFEnxf5uTEGp+3bzAbNOxU1paTgYS4ECU/IgfDw==",
      "dev": true,
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-validator-option": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-validator-option/-/helper-validator-option-7.16.7.tgz",
      "integrity": "sha512-TRtenOuRUVo9oIQGPC5G9DgK4743cdxvtOw0weQNpZXaS16SCBi5MNjZF8vba3ETURjZpTbVn7Vvcf2eAwFozQ==",
      "dev": true,
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-wrap-function": {
      "version": "7.16.8",
      "resolved": "https://registry.npmjs.org/@babel/helper-wrap-function/-/helper-wrap-function-7.16.8.tgz",
      "integrity": "sha512-8RpyRVIAW1RcDDGTA+GpPAwV22wXCfKOoM9bet6TLkGIFTkRQSkH1nMQ5Yet4MpoXe1ZwHPVtNasc2w0uZMqnw==",
      "dev": true,
      "dependencies": {
        "@babel/helper-function-name": "^7.16.7",
        "@babel/template": "^7.16.7",
        "@babel/traverse": "^7.16.8",
        "@babel/types": "^7.16.8"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-wrap-function/node_modules/@babel/template": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/template/-/template-7.16.7.tgz",
      "integrity": "sha512-I8j/x8kHUrbYRTUxXrrMbfCa7jxkE7tZre39x3kjr9hvI82cK1FfqLygotcWN5kdPGWcLdWMHpSBavse5tWw3w==",
      "dev": true,
      "dependencies": {
        "@babel/code-frame": "^7.16.7",
        "@babel/parser": "^7.16.7",
        "@babel/types": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helpers": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helpers/-/helpers-7.16.7.tgz",
      "integrity": "sha512-9ZDoqtfY7AuEOt3cxchfii6C7GDyyMBffktR5B2jvWv8u2+efwvpnVKXMWzNehqy68tKgAfSwfdw/lWpthS2bw==",
      "dev": true,
      "dependencies": {
        "@babel/template": "^7.16.7",
        "@babel/traverse": "^7.16.7",
        "@babel/types": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helpers/node_modules/@babel/template": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/template/-/template-7.16.7.tgz",
      "integrity": "sha512-I8j/x8kHUrbYRTUxXrrMbfCa7jxkE7tZre39x3kjr9hvI82cK1FfqLygotcWN5kdPGWcLdWMHpSBavse5tWw3w==",
      "dev": true,
      "dependencies": {
        "@babel/code-frame": "^7.16.7",
        "@babel/parser": "^7.16.7",
        "@babel/types": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/highlight": {
      "version": "7.16.10",
      "resolved": "https://registry.npmjs.org/@babel/highlight/-/highlight-7.16.10.tgz",
      "integrity": "sha512-5FnTQLSLswEj6IkgVw5KusNUUFY9ZGqe/TRFnP/BKYHYgfh7tc+C7mwiy95/yNP7Dh9x580Vv8r7u7ZfTBFxdw==",
      "dev": true,
      "dependencies": {
        "@babel/helper-validator-identifier": "^7.16.7",
        "chalk": "^2.0.0",
        "js-tokens": "^4.0.0"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/parser": {
      "version": "7.16.12",
      "resolved": "https://registry.npmjs.org/@babel/parser/-/parser-7.16.12.tgz",
      "integrity": "sha512-VfaV15po8RiZssrkPweyvbGVSe4x2y+aciFCgn0n0/SJMR22cwofRV1mtnJQYcSB1wUTaA/X1LnA3es66MCO5A==",
      "dev": true,
      "bin": {
        "parser": "bin/babel-parser.js"
      },
      "engines": {
        "node": ">=6.0.0"
      }
    },
    "node_modules/@babel/plugin-bugfix-safari-id-destructuring-collision-in-function-expression": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-bugfix-safari-id-destructuring-collision-in-function-expression/-/plugin-bugfix-safari-id-destructuring-collision-in-function-expression-7.16.7.tgz",
      "integrity": "sha512-anv/DObl7waiGEnC24O9zqL0pSuI9hljihqiDuFHC8d7/bjr/4RLGPWuc8rYOff/QPzbEPSkzG8wGG9aDuhHRg==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0"
      }
    },
    "node_modules/@babel/plugin-bugfix-v8-spread-parameters-in-optional-chaining": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-bugfix-v8-spread-parameters-in-optional-chaining/-/plugin-bugfix-v8-spread-parameters-in-optional-chaining-7.16.7.tgz",
      "integrity": "sha512-di8vUHRdf+4aJ7ltXhaDbPoszdkh59AQtJM5soLsuHpQJdFQZOA4uGj0V2u/CZ8bJ/u8ULDL5yq6FO/bCXnKHw==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/helper-skip-transparent-expression-wrappers": "^7.16.0",
        "@babel/plugin-proposal-optional-chaining": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.13.0"
      }
    },
    "node_modules/@babel/plugin-proposal-async-generator-functions": {
      "version": "7.16.4",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-async-generator-functions/-/plugin-proposal-async-generator-functions-7.16.4.tgz",
      "integrity": "sha512-/CUekqaAaZCQHleSK/9HajvcD/zdnJiKRiuUFq8ITE+0HsPzquf53cpFiqAwl/UfmJbR6n5uGPQSPdrmKOvHHg==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.14.5",
        "@babel/helper-remap-async-to-generator": "^7.16.4",
        "@babel/plugin-syntax-async-generators": "^7.8.4"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-proposal-class-properties": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-class-properties/-/plugin-proposal-class-properties-7.16.7.tgz",
      "integrity": "sha512-IobU0Xme31ewjYOShSIqd/ZGM/r/cuOz2z0MDbNrhF5FW+ZVgi0f2lyeoj9KFPDOAqsYxmLWZte1WOwlvY9aww==",
      "dev": true,
      "dependencies": {
        "@babel/helper-create-class-features-plugin": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-proposal-class-static-block": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-class-static-block/-/plugin-proposal-class-static-block-7.16.7.tgz",
      "integrity": "sha512-dgqJJrcZoG/4CkMopzhPJjGxsIe9A8RlkQLnL/Vhhx8AA9ZuaRwGSlscSh42hazc7WSrya/IK7mTeoF0DP9tEw==",
      "dev": true,
      "dependencies": {
        "@babel/helper-create-class-features-plugin": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/plugin-syntax-class-static-block": "^7.14.5"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.12.0"
      }
    },
    "node_modules/@babel/plugin-proposal-dynamic-import": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-dynamic-import/-/plugin-proposal-dynamic-import-7.16.7.tgz",
      "integrity": "sha512-I8SW9Ho3/8DRSdmDdH3gORdyUuYnk1m4cMxUAdu5oy4n3OfN8flDEH+d60iG7dUfi0KkYwSvoalHzzdRzpWHTg==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/plugin-syntax-dynamic-import": "^7.8.3"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-proposal-export-namespace-from": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-export-namespace-from/-/plugin-proposal-export-namespace-from-7.16.7.tgz",
      "integrity": "sha512-ZxdtqDXLRGBL64ocZcs7ovt71L3jhC1RGSyR996svrCi3PYqHNkb3SwPJCs8RIzD86s+WPpt2S73+EHCGO+NUA==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/plugin-syntax-export-namespace-from": "^7.8.3"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-proposal-json-strings": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-json-strings/-/plugin-proposal-json-strings-7.16.7.tgz",
      "integrity": "sha512-lNZ3EEggsGY78JavgbHsK9u5P3pQaW7k4axlgFLYkMd7UBsiNahCITShLjNQschPyjtO6dADrL24757IdhBrsQ==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/plugin-syntax-json-strings": "^7.8.3"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-proposal-logical-assignment-operators": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-logical-assignment-operators/-/plugin-proposal-logical-assignment-operators-7.16.7.tgz",
      "integrity": "sha512-K3XzyZJGQCr00+EtYtrDjmwX7o7PLK6U9bi1nCwkQioRFVUv6dJoxbQjtWVtP+bCPy82bONBKG8NPyQ4+i6yjg==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/plugin-syntax-logical-assignment-operators": "^7.10.4"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-proposal-nullish-coalescing-operator": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-nullish-coalescing-operator/-/plugin-proposal-nullish-coalescing-operator-7.16.7.tgz",
      "integrity": "sha512-aUOrYU3EVtjf62jQrCj63pYZ7k6vns2h/DQvHPWGmsJRYzWXZ6/AsfgpiRy6XiuIDADhJzP2Q9MwSMKauBQ+UQ==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/plugin-syntax-nullish-coalescing-operator": "^7.8.3"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-proposal-numeric-separator": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-numeric-separator/-/plugin-proposal-numeric-separator-7.16.7.tgz",
      "integrity": "sha512-vQgPMknOIgiuVqbokToyXbkY/OmmjAzr/0lhSIbG/KmnzXPGwW/AdhdKpi+O4X/VkWiWjnkKOBiqJrTaC98VKw==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/plugin-syntax-numeric-separator": "^7.10.4"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-proposal-object-rest-spread": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-object-rest-spread/-/plugin-proposal-object-rest-spread-7.16.7.tgz",
      "integrity": "sha512-3O0Y4+dw94HA86qSg9IHfyPktgR7q3gpNVAeiKQd+8jBKFaU5NQS1Yatgo4wY+UFNuLjvxcSmzcsHqrhgTyBUA==",
      "dev": true,
      "dependencies": {
        "@babel/compat-data": "^7.16.4",
        "@babel/helper-compilation-targets": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/plugin-syntax-object-rest-spread": "^7.8.3",
        "@babel/plugin-transform-parameters": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-proposal-optional-catch-binding": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-optional-catch-binding/-/plugin-proposal-optional-catch-binding-7.16.7.tgz",
      "integrity": "sha512-eMOH/L4OvWSZAE1VkHbr1vckLG1WUcHGJSLqqQwl2GaUqG6QjddvrOaTUMNYiv77H5IKPMZ9U9P7EaHwvAShfA==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/plugin-syntax-optional-catch-binding": "^7.8.3"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-proposal-optional-chaining": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-optional-chaining/-/plugin-proposal-optional-chaining-7.16.7.tgz",
      "integrity": "sha512-eC3xy+ZrUcBtP7x+sq62Q/HYd674pPTb/77XZMb5wbDPGWIdUbSr4Agr052+zaUPSb+gGRnjxXfKFvx5iMJ+DA==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/helper-skip-transparent-expression-wrappers": "^7.16.0",
        "@babel/plugin-syntax-optional-chaining": "^7.8.3"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-proposal-private-methods": {
      "version": "7.16.11",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-private-methods/-/plugin-proposal-private-methods-7.16.11.tgz",
      "integrity": "sha512-F/2uAkPlXDr8+BHpZvo19w3hLFKge+k75XUprE6jaqKxjGkSYcK+4c+bup5PdW/7W/Rpjwql7FTVEDW+fRAQsw==",
      "dev": true,
      "dependencies": {
        "@babel/helper-create-class-features-plugin": "^7.16.10",
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-proposal-private-property-in-object": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-private-property-in-object/-/plugin-proposal-private-property-in-object-7.16.7.tgz",
      "integrity": "sha512-rMQkjcOFbm+ufe3bTZLyOfsOUOxyvLXZJCTARhJr+8UMSoZmqTe1K1BgkFcrW37rAchWg57yI69ORxiWvUINuQ==",
      "dev": true,
      "dependencies": {
        "@babel/helper-annotate-as-pure": "^7.16.7",
        "@babel/helper-create-class-features-plugin": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/plugin-syntax-private-property-in-object": "^7.14.5"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-proposal-private-property-in-object/node_modules/@babel/helper-annotate-as-pure": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-annotate-as-pure/-/helper-annotate-as-pure-7.16.7.tgz",
      "integrity": "sha512-s6t2w/IPQVTAET1HitoowRGXooX8mCgtuP5195wD/QJPV6wYjpujCGF7JuMODVX2ZAJOf1GT6DT9MHEZvLOFSw==",
      "dev": true,
      "dependencies": {
        "@babel/types": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/plugin-proposal-unicode-property-regex": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-unicode-property-regex/-/plugin-proposal-unicode-property-regex-7.16.7.tgz",
      "integrity": "sha512-QRK0YI/40VLhNVGIjRNAAQkEHws0cswSdFFjpFyt943YmJIU1da9uW63Iu6NFV6CxTZW5eTDCrwZUstBWgp/Rg==",
      "dev": true,
      "dependencies": {
        "@babel/helper-create-regexp-features-plugin": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=4"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-syntax-async-generators": {
      "version": "7.8.4",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-async-generators/-/plugin-syntax-async-generators-7.8.4.tgz",
      "integrity": "sha512-tycmZxkGfZaxhMRbXlPXuVFpdWlXpir2W4AMhSJgRKzk/eDlIXOhb2LHWoLpDF7TEHylV5zNhykX6KAgHJmTNw==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.8.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-syntax-class-properties": {
      "version": "7.12.13",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-class-properties/-/plugin-syntax-class-properties-7.12.13.tgz",
      "integrity": "sha512-fm4idjKla0YahUNgFNLCB0qySdsoPiZP3iQE3rky0mBUtMZ23yDJ9SJdg6dXTSDnulOVqiF3Hgr9nbXvXTQZYA==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.12.13"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-syntax-class-static-block": {
      "version": "7.14.5",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-class-static-block/-/plugin-syntax-class-static-block-7.14.5.tgz",
      "integrity": "sha512-b+YyPmr6ldyNnM6sqYeMWE+bgJcJpO6yS4QD7ymxgH34GBPNDM/THBh8iunyvKIZztiwLH4CJZ0RxTk9emgpjw==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.14.5"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-syntax-dynamic-import": {
      "version": "7.8.3",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-dynamic-import/-/plugin-syntax-dynamic-import-7.8.3.tgz",
      "integrity": "sha512-5gdGbFon+PszYzqs83S3E5mpi7/y/8M9eC90MRTZfduQOYW76ig6SOSPNe41IG5LoP3FGBn2N0RjVDSQiS94kQ==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.8.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-syntax-export-namespace-from": {
      "version": "7.8.3",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-export-namespace-from/-/plugin-syntax-export-namespace-from-7.8.3.tgz",
      "integrity": "sha512-MXf5laXo6c1IbEbegDmzGPwGNTsHZmEy6QGznu5Sh2UCWvueywb2ee+CCE4zQiZstxU9BMoQO9i6zUFSY0Kj0Q==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.8.3"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-syntax-json-strings": {
      "version": "7.8.3",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-json-strings/-/plugin-syntax-json-strings-7.8.3.tgz",
      "integrity": "sha512-lY6kdGpWHvjoe2vk4WrAapEuBR69EMxZl+RoGRhrFGNYVK8mOPAW8VfbT/ZgrFbXlDNiiaxQnAtgVCZ6jv30EA==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.8.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-syntax-logical-assignment-operators": {
      "version": "7.10.4",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-logical-assignment-operators/-/plugin-syntax-logical-assignment-operators-7.10.4.tgz",
      "integrity": "sha512-d8waShlpFDinQ5MtvGU9xDAOzKH47+FFoney2baFIoMr952hKOLp1HR7VszoZvOsV/4+RRszNY7D17ba0te0ig==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.10.4"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-syntax-nullish-coalescing-operator": {
      "version": "7.8.3",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-nullish-coalescing-operator/-/plugin-syntax-nullish-coalescing-operator-7.8.3.tgz",
      "integrity": "sha512-aSff4zPII1u2QD7y+F8oDsz19ew4IGEJg9SVW+bqwpwtfFleiQDMdzA/R+UlWDzfnHFCxxleFT0PMIrR36XLNQ==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.8.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-syntax-numeric-separator": {
      "version": "7.10.4",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-numeric-separator/-/plugin-syntax-numeric-separator-7.10.4.tgz",
      "integrity": "sha512-9H6YdfkcK/uOnY/K7/aA2xpzaAgkQn37yzWUMRK7OaPOqOpGS1+n0H5hxT9AUw9EsSjPW8SVyMJwYRtWs3X3ug==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.10.4"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-syntax-object-rest-spread": {
      "version": "7.8.3",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-object-rest-spread/-/plugin-syntax-object-rest-spread-7.8.3.tgz",
      "integrity": "sha512-XoqMijGZb9y3y2XskN+P1wUGiVwWZ5JmoDRwx5+3GmEplNyVM2s2Dg8ILFQm8rWM48orGy5YpI5Bl8U1y7ydlA==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.8.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-syntax-optional-catch-binding": {
      "version": "7.8.3",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-optional-catch-binding/-/plugin-syntax-optional-catch-binding-7.8.3.tgz",
      "integrity": "sha512-6VPD0Pc1lpTqw0aKoeRTMiB+kWhAoT24PA+ksWSBrFtl5SIRVpZlwN3NNPQjehA2E/91FV3RjLWoVTglWcSV3Q==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.8.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-syntax-optional-chaining": {
      "version": "7.8.3",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-optional-chaining/-/plugin-syntax-optional-chaining-7.8.3.tgz",
      "integrity": "sha512-KoK9ErH1MBlCPxV0VANkXW2/dw4vlbGDrFgz8bmUsBGYkFRcbRwMh6cIJubdPrkxRwuGdtCk0v/wPTKbQgBjkg==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.8.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-syntax-private-property-in-object": {
      "version": "7.14.5",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-private-property-in-object/-/plugin-syntax-private-property-in-object-7.14.5.tgz",
      "integrity": "sha512-0wVnp9dxJ72ZUJDV27ZfbSj6iHLoytYZmh3rFcxNnvsJF3ktkzLDZPy/mA17HGsaQT3/DQsWYX1f1QGWkCoVUg==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.14.5"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-syntax-top-level-await": {
      "version": "7.14.5",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-top-level-await/-/plugin-syntax-top-level-await-7.14.5.tgz",
      "integrity": "sha512-hx++upLv5U1rgYfwe1xBQUhRmU41NEvpUvrp8jkrSCdvGSnM5/qdRMtylJ6PG5OFkBaHkbTAKTnd3/YyESRHFw==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.14.5"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-arrow-functions": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-arrow-functions/-/plugin-transform-arrow-functions-7.16.7.tgz",
      "integrity": "sha512-9ffkFFMbvzTvv+7dTp/66xvZAWASuPD5Tl9LK3Z9vhOmANo6j94rik+5YMBt4CwHVMWLWpMsriIc2zsa3WW3xQ==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-async-to-generator": {
      "version": "7.16.0",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-async-to-generator/-/plugin-transform-async-to-generator-7.16.0.tgz",
      "integrity": "sha512-PbIr7G9kR8tdH6g8Wouir5uVjklETk91GMVSUq+VaOgiinbCkBP6Q7NN/suM/QutZkMJMvcyAriogcYAdhg8Gw==",
      "dev": true,
      "dependencies": {
        "@babel/helper-module-imports": "^7.16.0",
        "@babel/helper-plugin-utils": "^7.14.5",
        "@babel/helper-remap-async-to-generator": "^7.16.0"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-block-scoped-functions": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-block-scoped-functions/-/plugin-transform-block-scoped-functions-7.16.7.tgz",
      "integrity": "sha512-JUuzlzmF40Z9cXyytcbZEZKckgrQzChbQJw/5PuEHYeqzCsvebDx0K0jWnIIVcmmDOAVctCgnYs0pMcrYj2zJg==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-block-scoping": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-block-scoping/-/plugin-transform-block-scoping-7.16.7.tgz",
      "integrity": "sha512-ObZev2nxVAYA4bhyusELdo9hb3H+A56bxH3FZMbEImZFiEDYVHXQSJ1hQKFlDnlt8G9bBrCZ5ZpURZUrV4G5qQ==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-classes": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-classes/-/plugin-transform-classes-7.16.7.tgz",
      "integrity": "sha512-WY7og38SFAGYRe64BrjKf8OrE6ulEHtr5jEYaZMwox9KebgqPi67Zqz8K53EKk1fFEJgm96r32rkKZ3qA2nCWQ==",
      "dev": true,
      "dependencies": {
        "@babel/helper-annotate-as-pure": "^7.16.7",
        "@babel/helper-environment-visitor": "^7.16.7",
        "@babel/helper-function-name": "^7.16.7",
        "@babel/helper-optimise-call-expression": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/helper-replace-supers": "^7.16.7",
        "@babel/helper-split-export-declaration": "^7.16.7",
        "globals": "^11.1.0"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-classes/node_modules/@babel/helper-annotate-as-pure": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-annotate-as-pure/-/helper-annotate-as-pure-7.16.7.tgz",
      "integrity": "sha512-s6t2w/IPQVTAET1HitoowRGXooX8mCgtuP5195wD/QJPV6wYjpujCGF7JuMODVX2ZAJOf1GT6DT9MHEZvLOFSw==",
      "dev": true,
      "dependencies": {
        "@babel/types": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/plugin-transform-computed-properties": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-computed-properties/-/plugin-transform-computed-properties-7.16.7.tgz",
      "integrity": "sha512-gN72G9bcmenVILj//sv1zLNaPyYcOzUho2lIJBMh/iakJ9ygCo/hEF9cpGb61SCMEDxbbyBoVQxrt+bWKu5KGw==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-destructuring": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-destructuring/-/plugin-transform-destructuring-7.16.7.tgz",
      "integrity": "sha512-VqAwhTHBnu5xBVDCvrvqJbtLUa++qZaWC0Fgr2mqokBlulZARGyIvZDoqbPlPaKImQ9dKAcCzbv+ul//uqu70A==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-dotall-regex": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-dotall-regex/-/plugin-transform-dotall-regex-7.16.7.tgz",
      "integrity": "sha512-Lyttaao2SjZF6Pf4vk1dVKv8YypMpomAbygW+mU5cYP3S5cWTfCJjG8xV6CFdzGFlfWK81IjL9viiTvpb6G7gQ==",
      "dev": true,
      "dependencies": {
        "@babel/helper-create-regexp-features-plugin": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-duplicate-keys": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-duplicate-keys/-/plugin-transform-duplicate-keys-7.16.7.tgz",
      "integrity": "sha512-03DvpbRfvWIXyK0/6QiR1KMTWeT6OcQ7tbhjrXyFS02kjuX/mu5Bvnh5SDSWHxyawit2g5aWhKwI86EE7GUnTw==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-exponentiation-operator": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-exponentiation-operator/-/plugin-transform-exponentiation-operator-7.16.7.tgz",
      "integrity": "sha512-8UYLSlyLgRixQvlYH3J2ekXFHDFLQutdy7FfFAMm3CPZ6q9wHCwnUyiXpQCe3gVVnQlHc5nsuiEVziteRNTXEA==",
      "dev": true,
      "dependencies": {
        "@babel/helper-builder-binary-assignment-operator-visitor": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-for-of": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-for-of/-/plugin-transform-for-of-7.16.7.tgz",
      "integrity": "sha512-/QZm9W92Ptpw7sjI9Nx1mbcsWz33+l8kuMIQnDwgQBG5s3fAfQvkRjQ7NqXhtNcKOnPkdICmUHyCaWW06HCsqg==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-function-name": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-function-name/-/plugin-transform-function-name-7.16.7.tgz",
      "integrity": "sha512-SU/C68YVwTRxqWj5kgsbKINakGag0KTgq9f2iZEXdStoAbOzLHEBRYzImmA6yFo8YZhJVflvXmIHUO7GWHmxxA==",
      "dev": true,
      "dependencies": {
        "@babel/helper-compilation-targets": "^7.16.7",
        "@babel/helper-function-name": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-literals": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-literals/-/plugin-transform-literals-7.16.7.tgz",
      "integrity": "sha512-6tH8RTpTWI0s2sV6uq3e/C9wPo4PTqqZps4uF0kzQ9/xPLFQtipynvmT1g/dOfEJ+0EQsHhkQ/zyRId8J2b8zQ==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-member-expression-literals": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-member-expression-literals/-/plugin-transform-member-expression-literals-7.16.7.tgz",
      "integrity": "sha512-mBruRMbktKQwbxaJof32LT9KLy2f3gH+27a5XSuXo6h7R3vqltl0PgZ80C8ZMKw98Bf8bqt6BEVi3svOh2PzMw==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-modules-amd": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-modules-amd/-/plugin-transform-modules-amd-7.16.7.tgz",
      "integrity": "sha512-KaaEtgBL7FKYwjJ/teH63oAmE3lP34N3kshz8mm4VMAw7U3PxjVwwUmxEFksbgsNUaO3wId9R2AVQYSEGRa2+g==",
      "dev": true,
      "dependencies": {
        "@babel/helper-module-transforms": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7",
        "babel-plugin-dynamic-import-node": "^2.3.3"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-modules-commonjs": {
      "version": "7.16.8",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-modules-commonjs/-/plugin-transform-modules-commonjs-7.16.8.tgz",
      "integrity": "sha512-oflKPvsLT2+uKQopesJt3ApiaIS2HW+hzHFcwRNtyDGieAeC/dIHZX8buJQ2J2X1rxGPy4eRcUijm3qcSPjYcA==",
      "dev": true,
      "dependencies": {
        "@babel/helper-module-transforms": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/helper-simple-access": "^7.16.7",
        "babel-plugin-dynamic-import-node": "^2.3.3"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-modules-systemjs": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-modules-systemjs/-/plugin-transform-modules-systemjs-7.16.7.tgz",
      "integrity": "sha512-DuK5E3k+QQmnOqBR9UkusByy5WZWGRxfzV529s9nPra1GE7olmxfqO2FHobEOYSPIjPBTr4p66YDcjQnt8cBmw==",
      "dev": true,
      "dependencies": {
        "@babel/helper-hoist-variables": "^7.16.7",
        "@babel/helper-module-transforms": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/helper-validator-identifier": "^7.16.7",
        "babel-plugin-dynamic-import-node": "^2.3.3"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-modules-umd": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-modules-umd/-/plugin-transform-modules-umd-7.16.7.tgz",
      "integrity": "sha512-EMh7uolsC8O4xhudF2F6wedbSHm1HHZ0C6aJ7K67zcDNidMzVcxWdGr+htW9n21klm+bOn+Rx4CBsAntZd3rEQ==",
      "dev": true,
      "dependencies": {
        "@babel/helper-module-transforms": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-named-capturing-groups-regex": {
      "version": "7.16.8",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-named-capturing-groups-regex/-/plugin-transform-named-capturing-groups-regex-7.16.8.tgz",
      "integrity": "sha512-j3Jw+n5PvpmhRR+mrgIh04puSANCk/T/UA3m3P1MjJkhlK906+ApHhDIqBQDdOgL/r1UYpz4GNclTXxyZrYGSw==",
      "dev": true,
      "dependencies": {
        "@babel/helper-create-regexp-features-plugin": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0"
      }
    },
    "node_modules/@babel/plugin-transform-new-target": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-new-target/-/plugin-transform-new-target-7.16.7.tgz",
      "integrity": "sha512-xiLDzWNMfKoGOpc6t3U+etCE2yRnn3SM09BXqWPIZOBpL2gvVrBWUKnsJx0K/ADi5F5YC5f8APFfWrz25TdlGg==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-object-super": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-object-super/-/plugin-transform-object-super-7.16.7.tgz",
      "integrity": "sha512-14J1feiQVWaGvRxj2WjyMuXS2jsBkgB3MdSN5HuC2G5nRspa5RK9COcs82Pwy5BuGcjb+fYaUj94mYcOj7rCvw==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/helper-replace-supers": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-parameters": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-parameters/-/plugin-transform-parameters-7.16.7.tgz",
      "integrity": "sha512-AT3MufQ7zZEhU2hwOA11axBnExW0Lszu4RL/tAlUJBuNoRak+wehQW8h6KcXOcgjY42fHtDxswuMhMjFEuv/aw==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-property-literals": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-property-literals/-/plugin-transform-property-literals-7.16.7.tgz",
      "integrity": "sha512-z4FGr9NMGdoIl1RqavCqGG+ZuYjfZ/hkCIeuH6Do7tXmSm0ls11nYVSJqFEUOSJbDab5wC6lRE/w6YjVcr6Hqw==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-regenerator": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-regenerator/-/plugin-transform-regenerator-7.16.7.tgz",
      "integrity": "sha512-mF7jOgGYCkSJagJ6XCujSQg+6xC1M77/03K2oBmVJWoFGNUtnVJO4WHKJk3dnPC8HCcj4xBQP1Egm8DWh3Pb3Q==",
      "dev": true,
      "dependencies": {
        "regenerator-transform": "^0.14.2"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-reserved-words": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-reserved-words/-/plugin-transform-reserved-words-7.16.7.tgz",
      "integrity": "sha512-KQzzDnZ9hWQBjwi5lpY5v9shmm6IVG0U9pB18zvMu2i4H90xpT4gmqwPYsn8rObiadYe2M0gmgsiOIF5A/2rtg==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-runtime": {
      "version": "7.16.4",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-runtime/-/plugin-transform-runtime-7.16.4.tgz",
      "integrity": "sha512-pru6+yHANMTukMtEZGC4fs7XPwg35v8sj5CIEmE+gEkFljFiVJxEWxx/7ZDkTK+iZRYo1bFXBtfIN95+K3cJ5A==",
      "dev": true,
      "dependencies": {
        "@babel/helper-module-imports": "^7.16.0",
        "@babel/helper-plugin-utils": "^7.14.5",
        "babel-plugin-polyfill-corejs2": "^0.3.0",
        "babel-plugin-polyfill-corejs3": "^0.4.0",
        "babel-plugin-polyfill-regenerator": "^0.3.0",
        "semver": "^6.3.0"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-runtime/node_modules/semver": {
      "version": "6.3.0",
      "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.0.tgz",
      "integrity": "sha512-b39TBaTSfV6yBrapU89p5fKekE2m/NwnDocOVruQFS1/veMgdzuPcnOM34M6CwxW8jH/lxEa5rBoDeUwu5HHTw==",
      "dev": true,
      "bin": {
        "semver": "bin/semver.js"
      }
    },
    "node_modules/@babel/plugin-transform-shorthand-properties": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-shorthand-properties/-/plugin-transform-shorthand-properties-7.16.7.tgz",
      "integrity": "sha512-hah2+FEnoRoATdIb05IOXf+4GzXYTq75TVhIn1PewihbpyrNWUt2JbudKQOETWw6QpLe+AIUpJ5MVLYTQbeeUg==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-spread": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-spread/-/plugin-transform-spread-7.16.7.tgz",
      "integrity": "sha512-+pjJpgAngb53L0iaA5gU/1MLXJIfXcYepLgXB3esVRf4fqmj8f2cxM3/FKaHsZms08hFQJkFccEWuIpm429TXg==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/helper-skip-transparent-expression-wrappers": "^7.16.0"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-sticky-regex": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-sticky-regex/-/plugin-transform-sticky-regex-7.16.7.tgz",
      "integrity": "sha512-NJa0Bd/87QV5NZZzTuZG5BPJjLYadeSZ9fO6oOUoL4iQx+9EEuw/eEM92SrsT19Yc2jgB1u1hsjqDtH02c3Drw==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-template-literals": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-template-literals/-/plugin-transform-template-literals-7.16.7.tgz",
      "integrity": "sha512-VwbkDDUeenlIjmfNeDX/V0aWrQH2QiVyJtwymVQSzItFDTpxfyJh3EVaQiS0rIN/CqbLGr0VcGmuwyTdZtdIsA==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-typeof-symbol": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-typeof-symbol/-/plugin-transform-typeof-symbol-7.16.7.tgz",
      "integrity": "sha512-p2rOixCKRJzpg9JB4gjnG4gjWkWa89ZoYUnl9snJ1cWIcTH/hvxZqfO+WjG6T8DRBpctEol5jw1O5rA8gkCokQ==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-unicode-escapes": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-unicode-escapes/-/plugin-transform-unicode-escapes-7.16.7.tgz",
      "integrity": "sha512-TAV5IGahIz3yZ9/Hfv35TV2xEm+kaBDaZQCn2S/hG9/CZ0DktxJv9eKfPc7yYCvOYR4JGx1h8C+jcSOvgaaI/Q==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-unicode-regex": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-unicode-regex/-/plugin-transform-unicode-regex-7.16.7.tgz",
      "integrity": "sha512-oC5tYYKw56HO75KZVLQ+R/Nl3Hro9kf8iG0hXoaHP7tjAyCpvqBiSNe6vGrZni1Z6MggmUOC6A7VP7AVmw225Q==",
      "dev": true,
      "dependencies": {
        "@babel/helper-create-regexp-features-plugin": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/preset-env": {
      "version": "7.16.4",
      "resolved": "https://registry.npmjs.org/@babel/preset-env/-/preset-env-7.16.4.tgz",
      "integrity": "sha512-v0QtNd81v/xKj4gNKeuAerQ/azeNn/G1B1qMLeXOcV8+4TWlD2j3NV1u8q29SDFBXx/NBq5kyEAO+0mpRgacjA==",
      "dev": true,
      "dependencies": {
        "@babel/compat-data": "^7.16.4",
        "@babel/helper-compilation-targets": "^7.16.3",
        "@babel/helper-plugin-utils": "^7.14.5",
        "@babel/helper-validator-option": "^7.14.5",
        "@babel/plugin-bugfix-safari-id-destructuring-collision-in-function-expression": "^7.16.2",
        "@babel/plugin-bugfix-v8-spread-parameters-in-optional-chaining": "^7.16.0",
        "@babel/plugin-proposal-async-generator-functions": "^7.16.4",
        "@babel/plugin-proposal-class-properties": "^7.16.0",
        "@babel/plugin-proposal-class-static-block": "^7.16.0",
        "@babel/plugin-proposal-dynamic-import": "^7.16.0",
        "@babel/plugin-proposal-export-namespace-from": "^7.16.0",
        "@babel/plugin-proposal-json-strings": "^7.16.0",
        "@babel/plugin-proposal-logical-assignment-operators": "^7.16.0",
        "@babel/plugin-proposal-nullish-coalescing-operator": "^7.16.0",
        "@babel/plugin-proposal-numeric-separator": "^7.16.0",
        "@babel/plugin-proposal-object-rest-spread": "^7.16.0",
        "@babel/plugin-proposal-optional-catch-binding": "^7.16.0",
        "@babel/plugin-proposal-optional-chaining": "^7.16.0",
        "@babel/plugin-proposal-private-methods": "^7.16.0",
        "@babel/plugin-proposal-private-property-in-object": "^7.16.0",
        "@babel/plugin-proposal-unicode-property-regex": "^7.16.0",
        "@babel/plugin-syntax-async-generators": "^7.8.4",
        "@babel/plugin-syntax-class-properties": "^7.12.13",
        "@babel/plugin-syntax-class-static-block": "^7.14.5",
        "@babel/plugin-syntax-dynamic-import": "^7.8.3",
        "@babel/plugin-syntax-export-namespace-from": "^7.8.3",
        "@babel/plugin-syntax-json-strings": "^7.8.3",
        "@babel/plugin-syntax-logical-assignment-operators": "^7.10.4",
        "@babel/plugin-syntax-nullish-coalescing-operator": "^7.8.3",
        "@babel/plugin-syntax-numeric-separator": "^7.10.4",
        "@babel/plugin-syntax-object-rest-spread": "^7.8.3",
        "@babel/plugin-syntax-optional-catch-binding": "^7.8.3",
        "@babel/plugin-syntax-optional-chaining": "^7.8.3",
        "@babel/plugin-syntax-private-property-in-object": "^7.14.5",
        "@babel/plugin-syntax-top-level-await": "^7.14.5",
        "@babel/plugin-transform-arrow-functions": "^7.16.0",
        "@babel/plugin-transform-async-to-generator": "^7.16.0",
        "@babel/plugin-transform-block-scoped-functions": "^7.16.0",
        "@babel/plugin-transform-block-scoping": "^7.16.0",
        "@babel/plugin-transform-classes": "^7.16.0",
        "@babel/plugin-transform-computed-properties": "^7.16.0",
        "@babel/plugin-transform-destructuring": "^7.16.0",
        "@babel/plugin-transform-dotall-regex": "^7.16.0",
        "@babel/plugin-transform-duplicate-keys": "^7.16.0",
        "@babel/plugin-transform-exponentiation-operator": "^7.16.0",
        "@babel/plugin-transform-for-of": "^7.16.0",
        "@babel/plugin-transform-function-name": "^7.16.0",
        "@babel/plugin-transform-literals": "^7.16.0",
        "@babel/plugin-transform-member-expression-literals": "^7.16.0",
        "@babel/plugin-transform-modules-amd": "^7.16.0",
        "@babel/plugin-transform-modules-commonjs": "^7.16.0",
        "@babel/plugin-transform-modules-systemjs": "^7.16.0",
        "@babel/plugin-transform-modules-umd": "^7.16.0",
        "@babel/plugin-transform-named-capturing-groups-regex": "^7.16.0",
        "@babel/plugin-transform-new-target": "^7.16.0",
        "@babel/plugin-transform-object-super": "^7.16.0",
        "@babel/plugin-transform-parameters": "^7.16.3",
        "@babel/plugin-transform-property-literals": "^7.16.0",
        "@babel/plugin-transform-regenerator": "^7.16.0",
        "@babel/plugin-transform-reserved-words": "^7.16.0",
        "@babel/plugin-transform-shorthand-properties": "^7.16.0",
        "@babel/plugin-transform-spread": "^7.16.0",
        "@babel/plugin-transform-sticky-regex": "^7.16.0",
        "@babel/plugin-transform-template-literals": "^7.16.0",
        "@babel/plugin-transform-typeof-symbol": "^7.16.0",
        "@babel/plugin-transform-unicode-escapes": "^7.16.0",
        "@babel/plugin-transform-unicode-regex": "^7.16.0",
        "@babel/preset-modules": "^0.1.5",
        "@babel/types": "^7.16.0",
        "babel-plugin-polyfill-corejs2": "^0.3.0",
        "babel-plugin-polyfill-corejs3": "^0.4.0",
        "babel-plugin-polyfill-regenerator": "^0.3.0",
        "core-js-compat": "^3.19.1",
        "semver": "^6.3.0"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/preset-env/node_modules/semver": {
      "version": "6.3.0",
      "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.0.tgz",
      "integrity": "sha512-b39TBaTSfV6yBrapU89p5fKekE2m/NwnDocOVruQFS1/veMgdzuPcnOM34M6CwxW8jH/lxEa5rBoDeUwu5HHTw==",
      "dev": true,
      "bin": {
        "semver": "bin/semver.js"
      }
    },
    "node_modules/@babel/preset-modules": {
      "version": "0.1.5",
      "resolved": "https://registry.npmjs.org/@babel/preset-modules/-/preset-modules-0.1.5.tgz",
      "integrity": "sha512-A57th6YRG7oR3cq/yt/Y84MvGgE0eJG2F1JLhKuyG+jFxEgrd/HAMJatiFtmOiZurz+0DkrvbheCLaV5f2JfjA==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.0.0",
        "@babel/plugin-proposal-unicode-property-regex": "^7.4.4",
        "@babel/plugin-transform-dotall-regex": "^7.4.4",
        "@babel/types": "^7.4.4",
        "esutils": "^2.0.2"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/runtime": {
      "version": "7.16.3",
      "resolved": "https://registry.npmjs.org/@babel/runtime/-/runtime-7.16.3.tgz",
      "integrity": "sha512-WBwekcqacdY2e9AF/Q7WLFUWmdJGJTkbjqTjoMDgXkVZ3ZRUvOPsLb5KdwISoQVsbP+DQzVZW4Zhci0DvpbNTQ==",
      "dev": true,
      "dependencies": {
        "regenerator-runtime": "^0.13.4"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/template": {
      "version": "7.16.0",
      "resolved": "https://registry.npmjs.org/@babel/template/-/template-7.16.0.tgz",
      "integrity": "sha512-MnZdpFD/ZdYhXwiunMqqgyZyucaYsbL0IrjoGjaVhGilz+x8YB++kRfygSOIj1yOtWKPlx7NBp+9I1RQSgsd5A==",
      "dev": true,
      "dependencies": {
        "@babel/code-frame": "^7.16.0",
        "@babel/parser": "^7.16.0",
        "@babel/types": "^7.16.0"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/traverse": {
      "version": "7.16.10",
      "resolved": "https://registry.npmjs.org/@babel/traverse/-/traverse-7.16.10.tgz",
      "integrity": "sha512-yzuaYXoRJBGMlBhsMJoUW7G1UmSb/eXr/JHYM/MsOJgavJibLwASijW7oXBdw3NQ6T0bW7Ty5P/VarOs9cHmqw==",
      "dev": true,
      "dependencies": {
        "@babel/code-frame": "^7.16.7",
        "@babel/generator": "^7.16.8",
        "@babel/helper-environment-visitor": "^7.16.7",
        "@babel/helper-function-name": "^7.16.7",
        "@babel/helper-hoist-variables": "^7.16.7",
        "@babel/helper-split-export-declaration": "^7.16.7",
        "@babel/parser": "^7.16.10",
        "@babel/types": "^7.16.8",
        "debug": "^4.1.0",
        "globals": "^11.1.0"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/traverse/node_modules/@babel/generator": {
      "version": "7.16.8",
      "resolved": "https://registry.npmjs.org/@babel/generator/-/generator-7.16.8.tgz",
      "integrity": "sha512-1ojZwE9+lOXzcWdWmO6TbUzDfqLD39CmEhN8+2cX9XkDo5yW1OpgfejfliysR2AWLpMamTiOiAp/mtroaymhpw==",
      "dev": true,
      "dependencies": {
        "@babel/types": "^7.16.8",
        "jsesc": "^2.5.1",
        "source-map": "^0.5.0"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/traverse/node_modules/source-map": {
      "version": "0.5.7",
      "resolved": "https://registry.npmjs.org/source-map/-/source-map-0.5.7.tgz",
      "integrity": "sha1-igOdLRAh0i0eoUyA2OpGi6LvP8w=",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/@babel/types": {
      "version": "7.16.8",
      "resolved": "https://registry.npmjs.org/@babel/types/-/types-7.16.8.tgz",
      "integrity": "sha512-smN2DQc5s4M7fntyjGtyIPbRJv6wW4rU/94fmYJ7PKQuZkC0qGMHXJbg6sNGt12JmVr4k5YaptI/XtiLJBnmIg==",
      "dev": true,
      "dependencies": {
        "@babel/helper-validator-identifier": "^7.16.7",
        "to-fast-properties": "^2.0.0"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@discoveryjs/json-ext": {
      "version": "0.5.6",
      "resolved": "https://registry.npmjs.org/@discoveryjs/json-ext/-/json-ext-0.5.6.tgz",
      "integrity": "sha512-ws57AidsDvREKrZKYffXddNkyaF14iHNHm8VQnZH6t99E8gczjNN0GpvcGny0imC80yQ0tHz1xVUKk/KFQSUyA==",
      "dev": true,
      "engines": {
        "node": ">=10.0.0"
      }
    },
    "node_modules/@gar/promisify": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/@gar/promisify/-/promisify-1.1.2.tgz",
      "integrity": "sha512-82cpyJyKRoQoRi+14ibCeGPu0CwypgtBAdBhq1WfvagpCZNKqwXbKwXllYSMG91DhmG4jt9gN8eP6lGOtozuaw==",
      "dev": true
    },
    "node_modules/@istanbuljs/load-nyc-config": {
      "version": "1.1.0",
      "resolved": "https://registry.npmjs.org/@istanbuljs/load-nyc-config/-/load-nyc-config-1.1.0.tgz",
      "integrity": "sha512-VjeHSlIzpv/NyD3N0YuHfXOPDIixcA1q2ZV98wsMqcYlPmv2n3Yb2lYP9XMElnaFVXg5A7YLTeLu6V84uQDjmQ==",
      "dev": true,
      "dependencies": {
        "camelcase": "^5.3.1",
        "find-up": "^4.1.0",
        "get-package-type": "^0.1.0",
        "js-yaml": "^3.13.1",
        "resolve-from": "^5.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/@istanbuljs/schema": {
      "version": "0.1.3",
      "resolved": "https://registry.npmjs.org/@istanbuljs/schema/-/schema-0.1.3.tgz",
      "integrity": "sha512-ZXRY4jNvVgSVQ8DL3LTcakaAtXwTVUxE81hslsyD2AtoXW/wVob10HkOJ1X/pAlcI7D+2YoZKg5do8G/w6RYgA==",
      "dev": true,
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/@jridgewell/resolve-uri": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/@jridgewell/resolve-uri/-/resolve-uri-1.0.0.tgz",
      "integrity": "sha512-9oLAnygRMi8Q5QkYEU4XWK04B+nuoXoxjRvRxgjuChkLZFBja0YPSgdZ7dZtwhncLBcQe/I/E+fLuk5qxcYVJA==",
      "dev": true,
      "engines": {
        "node": ">=6.0.0"
      }
    },
    "node_modules/@ngtools/webpack": {
      "version": "13.1.4",
      "resolved": "https://registry.npmjs.org/@ngtools/webpack/-/webpack-13.1.4.tgz",
      "integrity": "sha512-s8gzjG2nYHawFhlkHMkQWYrocHkBI1nF6T9K/oCSTIsq6kvTv//Ahno2VdBSgVq8uMnpv1TymvX0nFC4Dgn1HA==",
      "dev": true,
      "engines": {
        "node": "^12.20.0 || ^14.15.0 || >=16.10.0",
        "npm": "^6.11.0 || ^7.5.6 || >=8.0.0",
        "yarn": ">= 1.13.0"
      },
      "peerDependencies": {
        "@angular/compiler-cli": "^13.0.0 || ^13.1.0-next",
        "typescript": ">=4.4.3 <4.6",
        "webpack": "^5.30.0"
      }
    },
    "node_modules/@nodelib/fs.scandir": {
      "version": "2.1.5",
      "resolved": "https://registry.npmjs.org/@nodelib/fs.scandir/-/fs.scandir-2.1.5.tgz",
      "integrity": "sha512-vq24Bq3ym5HEQm2NKCr3yXDwjc7vTsEThRDnkp2DK9p1uqLR+DHurm/NOTo0KG7HYHU7eppKZj3MyqYuMBf62g==",
      "dev": true,
      "dependencies": {
        "@nodelib/fs.stat": "2.0.5",
        "run-parallel": "^1.1.9"
      },
      "engines": {
        "node": ">= 8"
      }
    },
    "node_modules/@nodelib/fs.stat": {
      "version": "2.0.5",
      "resolved": "https://registry.npmjs.org/@nodelib/fs.stat/-/fs.stat-2.0.5.tgz",
      "integrity": "sha512-RkhPPp2zrqDAQA/2jNhnztcPAlv64XdhIp7a7454A5ovI7Bukxgt7MX7udwAu3zg1DcpPU0rz3VV1SeaqvY4+A==",
      "dev": true,
      "engines": {
        "node": ">= 8"
      }
    },
    "node_modules/@nodelib/fs.walk": {
      "version": "1.2.8",
      "resolved": "https://registry.npmjs.org/@nodelib/fs.walk/-/fs.walk-1.2.8.tgz",
      "integrity": "sha512-oGB+UxlgWcgQkgwo8GcEGwemoTFt3FIO9ababBmaGwXIoBKZ+GTy0pP185beGg7Llih/NSHSV2XAs1lnznocSg==",
      "dev": true,
      "dependencies": {
        "@nodelib/fs.scandir": "2.1.5",
        "fastq": "^1.6.0"
      },
      "engines": {
        "node": ">= 8"
      }
    },
    "node_modules/@npmcli/fs": {
      "version": "1.1.0",
      "resolved": "https://registry.npmjs.org/@npmcli/fs/-/fs-1.1.0.tgz",
      "integrity": "sha512-VhP1qZLXcrXRIaPoqb4YA55JQxLNF3jNR4T55IdOJa3+IFJKNYHtPvtXx8slmeMavj37vCzCfrqQM1vWLsYKLA==",
      "dev": true,
      "dependencies": {
        "@gar/promisify": "^1.0.1",
        "semver": "^7.3.5"
      },
      "engines": {
        "node": "^12.13.0 || ^14.15.0 || >=16"
      }
    },
    "node_modules/@npmcli/git": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/@npmcli/git/-/git-2.1.0.tgz",
      "integrity": "sha512-/hBFX/QG1b+N7PZBFs0bi+evgRZcK9nWBxQKZkGoXUT5hJSwl5c4d7y8/hm+NQZRPhQ67RzFaj5UM9YeyKoryw==",
      "dev": true,
      "dependencies": {
        "@npmcli/promise-spawn": "^1.3.2",
        "lru-cache": "^6.0.0",
        "mkdirp": "^1.0.4",
        "npm-pick-manifest": "^6.1.1",
        "promise-inflight": "^1.0.1",
        "promise-retry": "^2.0.1",
        "semver": "^7.3.5",
        "which": "^2.0.2"
      }
    },
    "node_modules/@npmcli/git/node_modules/which": {
      "version": "2.0.2",
      "resolved": "https://registry.npmjs.org/which/-/which-2.0.2.tgz",
      "integrity": "sha512-BLI3Tl1TW3Pvl70l3yq3Y64i+awpwXqsGBYWkkqMtnbXgrMD+yj7rhW0kuEDxzJaYXGjEW5ogapKNMEKNMjibA==",
      "dev": true,
      "dependencies": {
        "isexe": "^2.0.0"
      },
      "bin": {
        "node-which": "bin/node-which"
      },
      "engines": {
        "node": ">= 8"
      }
    },
    "node_modules/@npmcli/installed-package-contents": {
      "version": "1.0.7",
      "resolved": "https://registry.npmjs.org/@npmcli/installed-package-contents/-/installed-package-contents-1.0.7.tgz",
      "integrity": "sha512-9rufe0wnJusCQoLpV9ZPKIVP55itrM5BxOXs10DmdbRfgWtHy1LDyskbwRnBghuB0PrF7pNPOqREVtpz4HqzKw==",
      "dev": true,
      "dependencies": {
        "npm-bundled": "^1.1.1",
        "npm-normalize-package-bin": "^1.0.1"
      },
      "bin": {
        "installed-package-contents": "index.js"
      },
      "engines": {
        "node": ">= 10"
      }
    },
    "node_modules/@npmcli/move-file": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/@npmcli/move-file/-/move-file-1.1.2.tgz",
      "integrity": "sha512-1SUf/Cg2GzGDyaf15aR9St9TWlb+XvbZXWpDx8YKs7MLzMH/BCeopv+y9vzrzgkfykCGuWOlSu3mZhj2+FQcrg==",
      "dev": true,
      "dependencies": {
        "mkdirp": "^1.0.4",
        "rimraf": "^3.0.2"
      },
      "engines": {
        "node": ">=10"
      }
    },
    "node_modules/@npmcli/node-gyp": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/@npmcli/node-gyp/-/node-gyp-1.0.3.tgz",
      "integrity": "sha512-fnkhw+fmX65kiLqk6E3BFLXNC26rUhK90zVwe2yncPliVT/Qos3xjhTLE59Df8KnPlcwIERXKVlU1bXoUQ+liA==",
      "dev": true
    },
    "node_modules/@npmcli/promise-spawn": {
      "version": "1.3.2",
      "resolved": "https://registry.npmjs.org/@npmcli/promise-spawn/-/promise-spawn-1.3.2.tgz",
      "integrity": "sha512-QyAGYo/Fbj4MXeGdJcFzZ+FkDkomfRBrPM+9QYJSg+PxgAUL+LU3FneQk37rKR2/zjqkCV1BLHccX98wRXG3Sg==",
      "dev": true,
      "dependencies": {
        "infer-owner": "^1.0.4"
      }
    },
    "node_modules/@npmcli/run-script": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/@npmcli/run-script/-/run-script-2.0.0.tgz",
      "integrity": "sha512-fSan/Pu11xS/TdaTpTB0MRn9guwGU8dye+x56mEVgBEd/QsybBbYcAL0phPXi8SGWFEChkQd6M9qL4y6VOpFig==",
      "dev": true,
      "dependencies": {
        "@npmcli/node-gyp": "^1.0.2",
        "@npmcli/promise-spawn": "^1.3.2",
        "node-gyp": "^8.2.0",
        "read-package-json-fast": "^2.0.1"
      }
    },
    "node_modules/@popperjs/core": {
      "version": "2.11.2",
      "resolved": "https://registry.npmjs.org/@popperjs/core/-/core-2.11.2.tgz",
      "integrity": "sha512-92FRmppjjqz29VMJ2dn+xdyXZBrMlE42AV6Kq6BwjWV7CNUW1hs2FtxSNLQE+gJhaZ6AAmYuO9y8dshhcBl7vA==",
      "peer": true,
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/popperjs"
      }
    },
    "node_modules/@schematics/angular": {
      "version": "13.1.4",
      "resolved": "https://registry.npmjs.org/@schematics/angular/-/angular-13.1.4.tgz",
      "integrity": "sha512-P1YsHn1LLAmdpB9X2TBuUgrvEW/KaoBbHr8ifYO8/uQEXyeiIF+So8h/dnegkYkdsr3OwQ2X/j3UF6/+HS0odg==",
      "dev": true,
      "dependencies": {
        "@angular-devkit/core": "13.1.4",
        "@angular-devkit/schematics": "13.1.4",
        "jsonc-parser": "3.0.0"
      },
      "engines": {
        "node": "^12.20.0 || ^14.15.0 || >=16.10.0",
        "npm": "^6.11.0 || ^7.5.6 || >=8.0.0",
        "yarn": ">= 1.13.0"
      }
    },
    "node_modules/@sindresorhus/is": {
      "version": "0.14.0",
      "resolved": "https://registry.npmjs.org/@sindresorhus/is/-/is-0.14.0.tgz",
      "integrity": "sha512-9NET910DNaIPngYnLLPeg+Ogzqsi9uM4mSboU5y6p8S5DzMTVEsJZrawi+BoDNUVBa2DhJqQYUFvMDfgU062LQ==",
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/@socket.io/base64-arraybuffer": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/@socket.io/base64-arraybuffer/-/base64-arraybuffer-1.0.2.tgz",
      "integrity": "sha512-dOlCBKnDw4iShaIsH/bxujKTM18+2TOAsYz+KSc11Am38H4q5Xw8Bbz97ZYdrVNM+um3p7w86Bvvmcn9q+5+eQ==",
      "dev": true,
      "engines": {
        "node": ">= 0.6.0"
      }
    },
    "node_modules/@szmarczak/http-timer": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/@szmarczak/http-timer/-/http-timer-1.1.2.tgz",
      "integrity": "sha512-XIB2XbzHTN6ieIjfIMV9hlVcfPU26s2vafYWQcZHWXHOxiaRZYEDKEwdl129Zyg50+foYV2jCgtrqSA6qNuNSA==",
      "dependencies": {
        "defer-to-connect": "^1.0.1"
      },
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/@tootallnate/once": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/@tootallnate/once/-/once-1.1.2.tgz",
      "integrity": "sha512-RbzJvlNzmRq5c3O09UipeuXno4tA1FE6ikOjxZK0tuxVv3412l64l5t1W5pj4+rJq9vpkm/kwiR07aZXnsKPxw==",
      "dev": true,
      "engines": {
        "node": ">= 6"
      }
    },
    "node_modules/@types/body-parser": {
      "version": "1.19.2",
      "resolved": "https://registry.npmjs.org/@types/body-parser/-/body-parser-1.19.2.tgz",
      "integrity": "sha512-ALYone6pm6QmwZoAgeyNksccT9Q4AWZQ6PvfwR37GT6r6FWUPguq6sUmNGSMV2Wr761oQoBxwGGa6DR5o1DC9g==",
      "dev": true,
      "peer": true,
      "dependencies": {
        "@types/connect": "*",
        "@types/node": "*"
      }
    },
    "node_modules/@types/component-emitter": {
      "version": "1.2.11",
      "resolved": "https://registry.npmjs.org/@types/component-emitter/-/component-emitter-1.2.11.tgz",
      "integrity": "sha512-SRXjM+tfsSlA9VuG8hGO2nft2p8zjXCK1VcC6N4NXbBbYbSia9kzCChYQajIjzIqOOOuh5Ock6MmV2oux4jDZQ==",
      "dev": true
    },
    "node_modules/@types/connect": {
      "version": "3.4.35",
      "resolved": "https://registry.npmjs.org/@types/connect/-/connect-3.4.35.tgz",
      "integrity": "sha512-cdeYyv4KWoEgpBISTxWvqYsVy444DOqehiF3fM3ne10AmJ62RSyNkUnxMJXHQWRQQX2eR94m5y1IZyDwBjV9FQ==",
      "dev": true,
      "peer": true,
      "dependencies": {
        "@types/node": "*"
      }
    },
    "node_modules/@types/cookie": {
      "version": "0.4.1",
      "resolved": "https://registry.npmjs.org/@types/cookie/-/cookie-0.4.1.tgz",
      "integrity": "sha512-XW/Aa8APYr6jSVVA1y/DEIZX0/GMKLEVekNG727R8cs56ahETkRAy/3DR7+fJyh7oUgGwNQaRfXCun0+KbWY7Q==",
      "dev": true
    },
    "node_modules/@types/cors": {
      "version": "2.8.12",
      "resolved": "https://registry.npmjs.org/@types/cors/-/cors-2.8.12.tgz",
      "integrity": "sha512-vt+kDhq/M2ayberEtJcIN/hxXy1Pk+59g2FV/ZQceeaTyCtCucjL2Q7FXlFjtWn4n15KCr1NE2lNNFhp0lEThw==",
      "dev": true
    },
    "node_modules/@types/eslint": {
      "version": "8.4.1",
      "resolved": "https://registry.npmjs.org/@types/eslint/-/eslint-8.4.1.tgz",
      "integrity": "sha512-GE44+DNEyxxh2Kc6ro/VkIj+9ma0pO0bwv9+uHSyBrikYOHr8zYcdPvnBOp1aw8s+CjRvuSx7CyWqRrNFQ59mA==",
      "dev": true,
      "dependencies": {
        "@types/estree": "*",
        "@types/json-schema": "*"
      }
    },
    "node_modules/@types/eslint-scope": {
      "version": "3.7.3",
      "resolved": "https://registry.npmjs.org/@types/eslint-scope/-/eslint-scope-3.7.3.tgz",
      "integrity": "sha512-PB3ldyrcnAicT35TWPs5IcwKD8S333HMaa2VVv4+wdvebJkjWuW/xESoB8IwRcog8HYVYamb1g/R31Qv5Bx03g==",
      "dev": true,
      "dependencies": {
        "@types/eslint": "*",
        "@types/estree": "*"
      }
    },
    "node_modules/@types/estree": {
      "version": "0.0.50",
      "resolved": "https://registry.npmjs.org/@types/estree/-/estree-0.0.50.tgz",
      "integrity": "sha512-C6N5s2ZFtuZRj54k2/zyRhNDjJwwcViAM3Nbm8zjBpbqAdZ00mr0CFxvSKeO8Y/e03WVFLpQMdHYVfUd6SB+Hw==",
      "dev": true
    },
    "node_modules/@types/express": {
      "version": "4.17.13",
      "resolved": "https://registry.npmjs.org/@types/express/-/express-4.17.13.tgz",
      "integrity": "sha512-6bSZTPaTIACxn48l50SR+axgrqm6qXFIxrdAKaG6PaJk3+zuUr35hBlgT7vOmJcum+OEaIBLtHV/qloEAFITeA==",
      "dev": true,
      "peer": true,
      "dependencies": {
        "@types/body-parser": "*",
        "@types/express-serve-static-core": "^4.17.18",
        "@types/qs": "*",
        "@types/serve-static": "*"
      }
    },
    "node_modules/@types/express-serve-static-core": {
      "version": "4.17.28",
      "resolved": "https://registry.npmjs.org/@types/express-serve-static-core/-/express-serve-static-core-4.17.28.tgz",
      "integrity": "sha512-P1BJAEAW3E2DJUlkgq4tOL3RyMunoWXqbSCygWo5ZIWTjUgN1YnaXWW4VWl/oc8vs/XoYibEGBKP0uZyF4AHig==",
      "dev": true,
      "peer": true,
      "dependencies": {
        "@types/node": "*",
        "@types/qs": "*",
        "@types/range-parser": "*"
      }
    },
    "node_modules/@types/http-proxy": {
      "version": "1.17.8",
      "resolved": "https://registry.npmjs.org/@types/http-proxy/-/http-proxy-1.17.8.tgz",
      "integrity": "sha512-5kPLG5BKpWYkw/LVOGWpiq3nEVqxiN32rTgI53Sk12/xHFQ2rG3ehI9IO+O3W2QoKeyB92dJkoka8SUm6BX1pA==",
      "dev": true,
      "dependencies": {
        "@types/node": "*"
      }
    },
    "node_modules/@types/jasmine": {
      "version": "3.10.3",
      "resolved": "https://registry.npmjs.org/@types/jasmine/-/jasmine-3.10.3.tgz",
      "integrity": "sha512-SWyMrjgdAUHNQmutvDcKablrJhkDLy4wunTme8oYLjKp41GnHGxMRXr2MQMvy/qy8H3LdzwQk9gH4hZ6T++H8g==",
      "dev": true
    },
    "node_modules/@types/json-schema": {
      "version": "7.0.9",
      "resolved": "https://registry.npmjs.org/@types/json-schema/-/json-schema-7.0.9.tgz",
      "integrity": "sha512-qcUXuemtEu+E5wZSJHNxUXeCZhAfXKQ41D+duX+VYPde7xyEVZci+/oXKJL13tnRs9lR2pr4fod59GT6/X1/yQ==",
      "dev": true
    },
    "node_modules/@types/mime": {
      "version": "1.3.2",
      "resolved": "https://registry.npmjs.org/@types/mime/-/mime-1.3.2.tgz",
      "integrity": "sha512-YATxVxgRqNH6nHEIsvg6k2Boc1JHI9ZbH5iWFFv/MTkchz3b1ieGDa5T0a9RznNdI0KhVbdbWSN+KWWrQZRxTw==",
      "dev": true,
      "peer": true
    },
    "node_modules/@types/node": {
      "version": "12.20.42",
      "resolved": "https://registry.npmjs.org/@types/node/-/node-12.20.42.tgz",
      "integrity": "sha512-aI3/oo5DzyiI5R/xAhxxRzfZlWlsbbqdgxfTPkqu/Zt+23GXiJvMCyPJT4+xKSXOnLqoL8jJYMLTwvK2M3a5hw==",
      "dev": true
    },
    "node_modules/@types/parse-json": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/@types/parse-json/-/parse-json-4.0.0.tgz",
      "integrity": "sha512-//oorEZjL6sbPcKUaCdIGlIUeH26mgzimjBB77G6XRgnDl/L5wOnpyBGRe/Mmf5CVW3PwEBE1NjiMZ/ssFh4wA==",
      "dev": true
    },
    "node_modules/@types/qs": {
      "version": "6.9.7",
      "resolved": "https://registry.npmjs.org/@types/qs/-/qs-6.9.7.tgz",
      "integrity": "sha512-FGa1F62FT09qcrueBA6qYTrJPVDzah9a+493+o2PCXsesWHIn27G98TsSMs3WPNbZIEj4+VJf6saSFpvD+3Zsw==",
      "dev": true,
      "peer": true
    },
    "node_modules/@types/range-parser": {
      "version": "1.2.4",
      "resolved": "https://registry.npmjs.org/@types/range-parser/-/range-parser-1.2.4.tgz",
      "integrity": "sha512-EEhsLsD6UsDM1yFhAvy0Cjr6VwmpMWqFBCb9w07wVugF7w9nfajxLuVmngTIpgS6svCnm6Vaw+MZhoDCKnOfsw==",
      "dev": true,
      "peer": true
    },
    "node_modules/@types/retry": {
      "version": "0.12.1",
      "resolved": "https://registry.npmjs.org/@types/retry/-/retry-0.12.1.tgz",
      "integrity": "sha512-xoDlM2S4ortawSWORYqsdU+2rxdh4LRW9ytc3zmT37RIKQh6IHyKwwtKhKis9ah8ol07DCkZxPt8BBvPjC6v4g==",
      "dev": true
    },
    "node_modules/@types/serve-static": {
      "version": "1.13.10",
      "resolved": "https://registry.npmjs.org/@types/serve-static/-/serve-static-1.13.10.tgz",
      "integrity": "sha512-nCkHGI4w7ZgAdNkrEu0bv+4xNV/XDqW+DydknebMOQwkpDGx8G+HTlj7R7ABI8i8nKxVw0wtKPi1D+lPOkh4YQ==",
      "dev": true,
      "peer": true,
      "dependencies": {
        "@types/mime": "^1",
        "@types/node": "*"
      }
    },
    "node_modules/@webassemblyjs/ast": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/ast/-/ast-1.11.1.tgz",
      "integrity": "sha512-ukBh14qFLjxTQNTXocdyksN5QdM28S1CxHt2rdskFyL+xFV7VremuBLVbmCePj+URalXBENx/9Lm7lnhihtCSw==",
      "dev": true,
      "dependencies": {
        "@webassemblyjs/helper-numbers": "1.11.1",
        "@webassemblyjs/helper-wasm-bytecode": "1.11.1"
      }
    },
    "node_modules/@webassemblyjs/floating-point-hex-parser": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/floating-point-hex-parser/-/floating-point-hex-parser-1.11.1.tgz",
      "integrity": "sha512-iGRfyc5Bq+NnNuX8b5hwBrRjzf0ocrJPI6GWFodBFzmFnyvrQ83SHKhmilCU/8Jv67i4GJZBMhEzltxzcNagtQ==",
      "dev": true
    },
    "node_modules/@webassemblyjs/helper-api-error": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/helper-api-error/-/helper-api-error-1.11.1.tgz",
      "integrity": "sha512-RlhS8CBCXfRUR/cwo2ho9bkheSXG0+NwooXcc3PAILALf2QLdFyj7KGsKRbVc95hZnhnERon4kW/D3SZpp6Tcg==",
      "dev": true
    },
    "node_modules/@webassemblyjs/helper-buffer": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/helper-buffer/-/helper-buffer-1.11.1.tgz",
      "integrity": "sha512-gwikF65aDNeeXa8JxXa2BAk+REjSyhrNC9ZwdT0f8jc4dQQeDQ7G4m0f2QCLPJiMTTO6wfDmRmj/pW0PsUvIcA==",
      "dev": true
    },
    "node_modules/@webassemblyjs/helper-numbers": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/helper-numbers/-/helper-numbers-1.11.1.tgz",
      "integrity": "sha512-vDkbxiB8zfnPdNK9Rajcey5C0w+QJugEglN0of+kmO8l7lDb77AnlKYQF7aarZuCrv+l0UvqL+68gSDr3k9LPQ==",
      "dev": true,
      "dependencies": {
        "@webassemblyjs/floating-point-hex-parser": "1.11.1",
        "@webassemblyjs/helper-api-error": "1.11.1",
        "@xtuc/long": "4.2.2"
      }
    },
    "node_modules/@webassemblyjs/helper-wasm-bytecode": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/helper-wasm-bytecode/-/helper-wasm-bytecode-1.11.1.tgz",
      "integrity": "sha512-PvpoOGiJwXeTrSf/qfudJhwlvDQxFgelbMqtq52WWiXC6Xgg1IREdngmPN3bs4RoO83PnL/nFrxucXj1+BX62Q==",
      "dev": true
    },
    "node_modules/@webassemblyjs/helper-wasm-section": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/helper-wasm-section/-/helper-wasm-section-1.11.1.tgz",
      "integrity": "sha512-10P9No29rYX1j7F3EVPX3JvGPQPae+AomuSTPiF9eBQeChHI6iqjMIwR9JmOJXwpnn/oVGDk7I5IlskuMwU/pg==",
      "dev": true,
      "dependencies": {
        "@webassemblyjs/ast": "1.11.1",
        "@webassemblyjs/helper-buffer": "1.11.1",
        "@webassemblyjs/helper-wasm-bytecode": "1.11.1",
        "@webassemblyjs/wasm-gen": "1.11.1"
      }
    },
    "node_modules/@webassemblyjs/ieee754": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/ieee754/-/ieee754-1.11.1.tgz",
      "integrity": "sha512-hJ87QIPtAMKbFq6CGTkZYJivEwZDbQUgYd3qKSadTNOhVY7p+gfP6Sr0lLRVTaG1JjFj+r3YchoqRYxNH3M0GQ==",
      "dev": true,
      "dependencies": {
        "@xtuc/ieee754": "^1.2.0"
      }
    },
    "node_modules/@webassemblyjs/leb128": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/leb128/-/leb128-1.11.1.tgz",
      "integrity": "sha512-BJ2P0hNZ0u+Th1YZXJpzW6miwqQUGcIHT1G/sf72gLVD9DZ5AdYTqPNbHZh6K1M5VmKvFXwGSWZADz+qBWxeRw==",
      "dev": true,
      "dependencies": {
        "@xtuc/long": "4.2.2"
      }
    },
    "node_modules/@webassemblyjs/utf8": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/utf8/-/utf8-1.11.1.tgz",
      "integrity": "sha512-9kqcxAEdMhiwQkHpkNiorZzqpGrodQQ2IGrHHxCy+Ozng0ofyMA0lTqiLkVs1uzTRejX+/O0EOT7KxqVPuXosQ==",
      "dev": true
    },
    "node_modules/@webassemblyjs/wasm-edit": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/wasm-edit/-/wasm-edit-1.11.1.tgz",
      "integrity": "sha512-g+RsupUC1aTHfR8CDgnsVRVZFJqdkFHpsHMfJuWQzWU3tvnLC07UqHICfP+4XyL2tnr1amvl1Sdp06TnYCmVkA==",
      "dev": true,
      "dependencies": {
        "@webassemblyjs/ast": "1.11.1",
        "@webassemblyjs/helper-buffer": "1.11.1",
        "@webassemblyjs/helper-wasm-bytecode": "1.11.1",
        "@webassemblyjs/helper-wasm-section": "1.11.1",
        "@webassemblyjs/wasm-gen": "1.11.1",
        "@webassemblyjs/wasm-opt": "1.11.1",
        "@webassemblyjs/wasm-parser": "1.11.1",
        "@webassemblyjs/wast-printer": "1.11.1"
      }
    },
    "node_modules/@webassemblyjs/wasm-gen": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/wasm-gen/-/wasm-gen-1.11.1.tgz",
      "integrity": "sha512-F7QqKXwwNlMmsulj6+O7r4mmtAlCWfO/0HdgOxSklZfQcDu0TpLiD1mRt/zF25Bk59FIjEuGAIyn5ei4yMfLhA==",
      "dev": true,
      "dependencies": {
        "@webassemblyjs/ast": "1.11.1",
        "@webassemblyjs/helper-wasm-bytecode": "1.11.1",
        "@webassemblyjs/ieee754": "1.11.1",
        "@webassemblyjs/leb128": "1.11.1",
        "@webassemblyjs/utf8": "1.11.1"
      }
    },
    "node_modules/@webassemblyjs/wasm-opt": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/wasm-opt/-/wasm-opt-1.11.1.tgz",
      "integrity": "sha512-VqnkNqnZlU5EB64pp1l7hdm3hmQw7Vgqa0KF/KCNO9sIpI6Fk6brDEiX+iCOYrvMuBWDws0NkTOxYEb85XQHHw==",
      "dev": true,
      "dependencies": {
        "@webassemblyjs/ast": "1.11.1",
        "@webassemblyjs/helper-buffer": "1.11.1",
        "@webassemblyjs/wasm-gen": "1.11.1",
        "@webassemblyjs/wasm-parser": "1.11.1"
      }
    },
    "node_modules/@webassemblyjs/wasm-parser": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/wasm-parser/-/wasm-parser-1.11.1.tgz",
      "integrity": "sha512-rrBujw+dJu32gYB7/Lup6UhdkPx9S9SnobZzRVL7VcBH9Bt9bCBLEuX/YXOOtBsOZ4NQrRykKhffRWHvigQvOA==",
      "dev": true,
      "dependencies": {
        "@webassemblyjs/ast": "1.11.1",
        "@webassemblyjs/helper-api-error": "1.11.1",
        "@webassemblyjs/helper-wasm-bytecode": "1.11.1",
        "@webassemblyjs/ieee754": "1.11.1",
        "@webassemblyjs/leb128": "1.11.1",
        "@webassemblyjs/utf8": "1.11.1"
      }
    },
    "node_modules/@webassemblyjs/wast-printer": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/wast-printer/-/wast-printer-1.11.1.tgz",
      "integrity": "sha512-IQboUWM4eKzWW+N/jij2sRatKMh99QEelo3Eb2q0qXkvPRISAj8Qxtmw5itwqK+TTkBuUIE45AxYPToqPtL5gg==",
      "dev": true,
      "dependencies": {
        "@webassemblyjs/ast": "1.11.1",
        "@xtuc/long": "4.2.2"
      }
    },
    "node_modules/@xtuc/ieee754": {
      "version": "1.2.0",
      "resolved": "https://registry.npmjs.org/@xtuc/ieee754/-/ieee754-1.2.0.tgz",
      "integrity": "sha512-DX8nKgqcGwsc0eJSqYt5lwP4DH5FlHnmuWWBRy7X0NcaGR0ZtuyeESgMwTYVEtxmsNGY+qit4QYT/MIYTOTPeA==",
      "dev": true
    },
    "node_modules/@xtuc/long": {
      "version": "4.2.2",
      "resolved": "https://registry.npmjs.org/@xtuc/long/-/long-4.2.2.tgz",
      "integrity": "sha512-NuHqBY1PB/D8xU6s/thBgOAiAP7HOYDQ32+BFZILJ8ivkUkAHQnWfn6WhL79Owj1qmUnoN/YPhktdIoucipkAQ==",
      "dev": true
    },
    "node_modules/@yarnpkg/lockfile": {
      "version": "1.1.0",
      "resolved": "https://registry.npmjs.org/@yarnpkg/lockfile/-/lockfile-1.1.0.tgz",
      "integrity": "sha512-GpSwvyXOcOOlV70vbnzjj4fW5xW/FdUF6nQEt1ENy7m4ZCczi1+/buVUPAqmGfqznsORNFzUMjctTIp8a9tuCQ==",
      "dev": true
    },
    "node_modules/abab": {
      "version": "2.0.5",
      "resolved": "https://registry.npmjs.org/abab/-/abab-2.0.5.tgz",
      "integrity": "sha512-9IK9EadsbHo6jLWIpxpR6pL0sazTXV6+SQv25ZB+F7Bj9mJNaOc4nCRabwd5M/JwmUa8idz6Eci6eKfJryPs6Q==",
      "dev": true
    },
    "node_modules/abbrev": {
      "version": "1.1.1",
      "resolved": "https://registry.npmjs.org/abbrev/-/abbrev-1.1.1.tgz",
      "integrity": "sha512-nne9/IiQ/hzIhY6pdDnbBtz7DjPTKrY00P/zvPSm5pOFkl6xuGrGnXn/VtTNNfNtAfZ9/1RtehkszU9qcTii0Q==",
      "dev": true
    },
    "node_modules/accepts": {
      "version": "1.3.7",
      "resolved": "https://registry.npmjs.org/accepts/-/accepts-1.3.7.tgz",
      "integrity": "sha512-Il80Qs2WjYlJIBNzNkK6KYqlVMTbZLXgHx2oT0pU/fjRHyEp+PEfEPY0R3WCwAGVOtauxh1hOxNgIf5bv7dQpA==",
      "dependencies": {
        "mime-types": "~2.1.24",
        "negotiator": "0.6.2"
      },
      "engines": {
        "node": ">= 0.6"
      }
    },
    "node_modules/accepts/node_modules/negotiator": {
      "version": "0.6.2",
      "resolved": "https://registry.npmjs.org/negotiator/-/negotiator-0.6.2.tgz",
      "integrity": "sha512-hZXc7K2e+PgeI1eDBe/10Ard4ekbfrrqG8Ep+8Jmf4JID2bNg7NvCPOZN+kfF574pFQI7mum2AUqDidoKqcTOw==",
      "engines": {
        "node": ">= 0.6"
      }
    },
    "node_modules/acorn": {
      "version": "8.7.0",
      "resolved": "https://registry.npmjs.org/acorn/-/acorn-8.7.0.tgz",
      "integrity": "sha512-V/LGr1APy+PXIwKebEWrkZPwoeoF+w1jiOBUmuxuiUIaOHtob8Qc9BTrYo7VuI5fR8tqsy+buA2WFooR5olqvQ==",
      "dev": true,
      "bin": {
        "acorn": "bin/acorn"
      },
      "engines": {
        "node": ">=0.4.0"
      }
    },
    "node_modules/acorn-import-assertions": {
      "version": "1.8.0",
      "resolved": "https://registry.npmjs.org/acorn-import-assertions/-/acorn-import-assertions-1.8.0.tgz",
      "integrity": "sha512-m7VZ3jwz4eK6A4Vtt8Ew1/mNbP24u0FhdyfA7fSvnJR6LMdfOYnmuIrrJAgrYfYJ10F/otaHTtrtrtmHdMNzEw==",
      "dev": true,
      "peerDependencies": {
        "acorn": "^8"
      }
    },
    "node_modules/adjust-sourcemap-loader": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/adjust-sourcemap-loader/-/adjust-sourcemap-loader-4.0.0.tgz",
      "integrity": "sha512-OXwN5b9pCUXNQHJpwwD2qP40byEmSgzj8B4ydSN0uMNYWiFmJ6x6KwUllMmfk8Rwu/HJDFR7U8ubsWBoN0Xp0A==",
      "dev": true,
      "dependencies": {
        "loader-utils": "^2.0.0",
        "regex-parser": "^2.2.11"
      },
      "engines": {
        "node": ">=8.9"
      }
    },
    "node_modules/adjust-sourcemap-loader/node_modules/loader-utils": {
      "version": "2.0.2",
      "resolved": "https://registry.npmjs.org/loader-utils/-/loader-utils-2.0.2.tgz",
      "integrity": "sha512-TM57VeHptv569d/GKh6TAYdzKblwDNiumOdkFnejjD0XwTH87K90w3O7AiJRqdQoXygvi1VQTJTLGhJl7WqA7A==",
      "dev": true,
      "dependencies": {
        "big.js": "^5.2.2",
        "emojis-list": "^3.0.0",
        "json5": "^2.1.2"
      },
      "engines": {
        "node": ">=8.9.0"
      }
    },
    "node_modules/agent-base": {
      "version": "6.0.2",
      "resolved": "https://registry.npmjs.org/agent-base/-/agent-base-6.0.2.tgz",
      "integrity": "sha512-RZNwNclF7+MS/8bDg70amg32dyeZGZxiDuQmZxKLAlQjr3jGyLx+4Kkk58UO7D2QdgFIQCovuSuZESne6RG6XQ==",
      "dev": true,
      "dependencies": {
        "debug": "4"
      },
      "engines": {
        "node": ">= 6.0.0"
      }
    },
    "node_modules/agentkeepalive": {
      "version": "4.2.0",
      "resolved": "https://registry.npmjs.org/agentkeepalive/-/agentkeepalive-4.2.0.tgz",
      "integrity": "sha512-0PhAp58jZNw13UJv7NVdTGb0ZcghHUb3DrZ046JiiJY/BOaTTpbwdHq2VObPCBV8M2GPh7sgrJ3AQ8Ey468LJw==",
      "dev": true,
      "dependencies": {
        "debug": "^4.1.0",
        "depd": "^1.1.2",
        "humanize-ms": "^1.2.1"
      },
      "engines": {
        "node": ">= 8.0.0"
      }
    },
    "node_modules/aggregate-error": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/aggregate-error/-/aggregate-error-3.1.0.tgz",
      "integrity": "sha512-4I7Td01quW/RpocfNayFdFVk1qSuoh0E7JrbRJ16nH01HhKFQ88INq9Sd+nd72zqRySlr9BmDA8xlEJ6vJMrYA==",
      "dev": true,
      "dependencies": {
        "clean-stack": "^2.0.0",
        "indent-string": "^4.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/ajv": {
      "version": "8.8.2",
      "resolved": "https://registry.npmjs.org/ajv/-/ajv-8.8.2.tgz",
      "integrity": "sha512-x9VuX+R/jcFj1DHo/fCp99esgGDWiHENrKxaCENuCxpoMCmAt/COCGVDwA7kleEpEzJjDnvh3yGoOuLu0Dtllw==",
      "dev": true,
      "dependencies": {
        "fast-deep-equal": "^3.1.1",
        "json-schema-traverse": "^1.0.0",
        "require-from-string": "^2.0.2",
        "uri-js": "^4.2.2"
      },
      "funding": {
        "type": "github",
        "url": "https://github.com/sponsors/epoberezkin"
      }
    },
    "node_modules/ajv-formats": {
      "version": "2.1.1",
      "resolved": "https://registry.npmjs.org/ajv-formats/-/ajv-formats-2.1.1.tgz",
      "integrity": "sha512-Wx0Kx52hxE7C18hkMEggYlEifqWZtYaRgouJor+WMdPnQyEK13vgEWyVNup7SoeeoLMsr4kf5h6dOW11I15MUA==",
      "dev": true,
      "dependencies": {
        "ajv": "^8.0.0"
      },
      "peerDependencies": {
        "ajv": "^8.0.0"
      },
      "peerDependenciesMeta": {
        "ajv": {
          "optional": true
        }
      }
    },
    "node_modules/ajv-keywords": {
      "version": "5.1.0",
      "resolved": "https://registry.npmjs.org/ajv-keywords/-/ajv-keywords-5.1.0.tgz",
      "integrity": "sha512-YCS/JNFAUyr5vAuhk1DWm1CBxRHW9LbJ2ozWeemrIqpbsqKjHVxYPyi5GC0rjZIT5JxJ3virVTS8wk4i/Z+krw==",
      "dev": true,
      "dependencies": {
        "fast-deep-equal": "^3.1.3"
      },
      "peerDependencies": {
        "ajv": "^8.8.2"
      }
    },
    "node_modules/ansi-align": {
      "version": "3.0.1",
      "resolved": "https://registry.npmjs.org/ansi-align/-/ansi-align-3.0.1.tgz",
      "integrity": "sha512-IOfwwBF5iczOjp/WeY4YxyjqAFMQoZufdQWDd19SEExbVLNXqvpzSJ/M7Za4/sCPmQ0+GRquoA7bGcINcxew6w==",
      "dependencies": {
        "string-width": "^4.1.0"
      }
    },
    "node_modules/ansi-colors": {
      "version": "4.1.1",
      "resolved": "https://registry.npmjs.org/ansi-colors/-/ansi-colors-4.1.1.tgz",
      "integrity": "sha512-JoX0apGbHaUJBNl6yF+p6JAFYZ666/hhCGKN5t9QFjbJQKUU/g8MNbFDbvfrgKXvI1QpZplPOnwIo99lX/AAmA==",
      "dev": true,
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/ansi-escapes": {
      "version": "4.3.2",
      "resolved": "https://registry.npmjs.org/ansi-escapes/-/ansi-escapes-4.3.2.tgz",
      "integrity": "sha512-gKXj5ALrKWQLsYG9jlTRmR/xKluxHV+Z9QEwNIgCfM1/uwPMCuzVVnh5mwTd+OuBZcwSIMbqssNWRm1lE51QaQ==",
      "dev": true,
      "dependencies": {
        "type-fest": "^0.21.3"
      },
      "engines": {
        "node": ">=8"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/ansi-html-community": {
      "version": "0.0.8",
      "resolved": "https://registry.npmjs.org/ansi-html-community/-/ansi-html-community-0.0.8.tgz",
      "integrity": "sha512-1APHAyr3+PCamwNw3bXCPp4HFLONZt/yIH0sZp0/469KWNTEy+qN5jQ3GVX6DMZ1UXAi34yVwtTeaG/HpBuuzw==",
      "dev": true,
      "engines": [
        "node >= 0.8.0"
      ],
      "bin": {
        "ansi-html": "bin/ansi-html"
      }
    },
    "node_modules/ansi-regex": {
      "version": "5.0.1",
      "resolved": "https://registry.npmjs.org/ansi-regex/-/ansi-regex-5.0.1.tgz",
      "integrity": "sha512-quJQXlTSUGL2LH9SUXo8VwsY4soanhgo6LNSm84E1LBcE8s3O0wpdiRzyR9z/ZZJMlMWv37qOOb9pdJlMUEKFQ==",
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/ansi-styles": {
      "version": "3.2.1",
      "resolved": "https://registry.npmjs.org/ansi-styles/-/ansi-styles-3.2.1.tgz",
      "integrity": "sha512-VT0ZI6kZRdTh8YyJw3SMbYm/u+NqfsAxEpWO0Pf9sq8/e94WxxOpPKx9FR1FlyCtOVDNOQ+8ntlqFxiRc+r5qA==",
      "dev": true,
      "dependencies": {
        "color-convert": "^1.9.0"
      },
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/anymatch": {
      "version": "3.1.2",
      "resolved": "https://registry.npmjs.org/anymatch/-/anymatch-3.1.2.tgz",
      "integrity": "sha512-P43ePfOAIupkguHUycrc4qJ9kz8ZiuOUijaETwX7THt0Y/GNK7v0aa8rY816xWjZ7rJdA5XdMcpVFTKMq+RvWg==",
      "dev": true,
      "dependencies": {
        "normalize-path": "^3.0.0",
        "picomatch": "^2.0.4"
      },
      "engines": {
        "node": ">= 8"
      }
    },
    "node_modules/aproba": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/aproba/-/aproba-2.0.0.tgz",
      "integrity": "sha512-lYe4Gx7QT+MKGbDsA+Z+he/Wtef0BiwDOlK/XkBrdfsh9J/jPPXbX0tE9x9cl27Tmu5gg3QUbUrQYa/y+KOHPQ==",
      "dev": true
    },
    "node_modules/are-we-there-yet": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/are-we-there-yet/-/are-we-there-yet-2.0.0.tgz",
      "integrity": "sha512-Ci/qENmwHnsYo9xKIcUJN5LeDKdJ6R1Z1j9V/J5wyq8nh/mYPEpIKJbBZXtZjG04HiK7zV/p6Vs9952MrMeUIw==",
      "dev": true,
      "dependencies": {
        "delegates": "^1.0.0",
        "readable-stream": "^3.6.0"
      },
      "engines": {
        "node": ">=10"
      }
    },
    "node_modules/argparse": {
      "version": "1.0.10",
      "resolved": "https://registry.npmjs.org/argparse/-/argparse-1.0.10.tgz",
      "integrity": "sha512-o5Roy6tNG4SL/FOkCAN6RzjiakZS25RLYFrcMttJqbdd8BWrnA+fGz57iN5Pb06pvBGvl5gQ0B48dJlslXvoTg==",
      "dev": true,
      "dependencies": {
        "sprintf-js": "~1.0.2"
      }
    },
    "node_modules/array-flatten": {
      "version": "2.1.2",
      "resolved": "https://registry.npmjs.org/array-flatten/-/array-flatten-2.1.2.tgz",
      "integrity": "sha512-hNfzcOV8W4NdualtqBFPyVO+54DSJuZGY9qT4pRroB6S9e3iiido2ISIC5h9R2sPJ8H3FHCIiEnsv1lPXO3KtQ==",
      "dev": true
    },
    "node_modules/array-union": {
      "version": "3.0.1",
      "resolved": "https://registry.npmjs.org/array-union/-/array-union-3.0.1.tgz",
      "integrity": "sha512-1OvF9IbWwaeiM9VhzYXVQacMibxpXOMYVNIvMtKRyX9SImBXpKcFr8XvFDeEslCyuH/t6KRt7HEO94AlP8Iatw==",
      "dev": true,
      "engines": {
        "node": ">=12"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/async": {
      "version": "2.6.3",
      "resolved": "https://registry.npmjs.org/async/-/async-2.6.3.tgz",
      "integrity": "sha512-zflvls11DCy+dQWzTW2dzuilv8Z5X/pjfmZOWba6TNIVDm+2UDaJmXSOXlasHKfNBs8oo3M0aT50fDEWfKZjXg==",
      "dev": true,
      "dependencies": {
        "lodash": "^4.17.14"
      }
    },
    "node_modules/atob": {
      "version": "2.1.2",
      "resolved": "https://registry.npmjs.org/atob/-/atob-2.1.2.tgz",
      "integrity": "sha512-Wm6ukoaOGJi/73p/cl2GvLjTI5JM1k/O14isD73YML8StrH/7/lRFgmg8nICZgD3bZZvjwCGxtMOD3wWNAu8cg==",
      "dev": true,
      "bin": {
        "atob": "bin/atob.js"
      },
      "engines": {
        "node": ">= 4.5.0"
      }
    },
    "node_modules/autoprefixer": {
      "version": "10.4.2",
      "resolved": "https://registry.npmjs.org/autoprefixer/-/autoprefixer-10.4.2.tgz",
      "integrity": "sha512-9fOPpHKuDW1w/0EKfRmVnxTDt8166MAnLI3mgZ1JCnhNtYWxcJ6Ud5CO/AVOZi/AvFa8DY9RTy3h3+tFBlrrdQ==",
      "dev": true,
      "dependencies": {
        "browserslist": "^4.19.1",
        "caniuse-lite": "^1.0.30001297",
        "fraction.js": "^4.1.2",
        "normalize-range": "^0.1.2",
        "picocolors": "^1.0.0",
        "postcss-value-parser": "^4.2.0"
      },
      "bin": {
        "autoprefixer": "bin/autoprefixer"
      },
      "engines": {
        "node": "^10 || ^12 || >=14"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/postcss/"
      },
      "peerDependencies": {
        "postcss": "^8.1.0"
      }
    },
    "node_modules/babel-loader": {
      "version": "8.2.3",
      "resolved": "https://registry.npmjs.org/babel-loader/-/babel-loader-8.2.3.tgz",
      "integrity": "sha512-n4Zeta8NC3QAsuyiizu0GkmRcQ6clkV9WFUnUf1iXP//IeSKbWjofW3UHyZVwlOB4y039YQKefawyTn64Zwbuw==",
      "dev": true,
      "dependencies": {
        "find-cache-dir": "^3.3.1",
        "loader-utils": "^1.4.0",
        "make-dir": "^3.1.0",
        "schema-utils": "^2.6.5"
      },
      "engines": {
        "node": ">= 8.9"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0",
        "webpack": ">=2"
      }
    },
    "node_modules/babel-loader/node_modules/json5": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/json5/-/json5-1.0.1.tgz",
      "integrity": "sha512-aKS4WQjPenRxiQsC93MNfjx+nbF4PAdYzmd/1JIj8HYzqfbu86beTuNgXDzPknWk0n0uARlyewZo4s++ES36Ow==",
      "dev": true,
      "dependencies": {
        "minimist": "^1.2.0"
      },
      "bin": {
        "json5": "lib/cli.js"
      }
    },
    "node_modules/babel-loader/node_modules/loader-utils": {
      "version": "1.4.0",
      "resolved": "https://registry.npmjs.org/loader-utils/-/loader-utils-1.4.0.tgz",
      "integrity": "sha512-qH0WSMBtn/oHuwjy/NucEgbx5dbxxnxup9s4PVXJUDHZBQY+s0NWA9rJf53RBnQZxfch7euUui7hpoAPvALZdA==",
      "dev": true,
      "dependencies": {
        "big.js": "^5.2.2",
        "emojis-list": "^3.0.0",
        "json5": "^1.0.1"
      },
      "engines": {
        "node": ">=4.0.0"
      }
    },
    "node_modules/babel-plugin-dynamic-import-node": {
      "version": "2.3.3",
      "resolved": "https://registry.npmjs.org/babel-plugin-dynamic-import-node/-/babel-plugin-dynamic-import-node-2.3.3.tgz",
      "integrity": "sha512-jZVI+s9Zg3IqA/kdi0i6UDCybUI3aSBLnglhYbSSjKlV7yF1F/5LWv8MakQmvYpnbJDS6fcBL2KzHSxNCMtWSQ==",
      "dev": true,
      "dependencies": {
        "object.assign": "^4.1.0"
      }
    },
    "node_modules/babel-plugin-istanbul": {
      "version": "6.1.1",
      "resolved": "https://registry.npmjs.org/babel-plugin-istanbul/-/babel-plugin-istanbul-6.1.1.tgz",
      "integrity": "sha512-Y1IQok9821cC9onCx5otgFfRm7Lm+I+wwxOx738M/WLPZ9Q42m4IG5W0FNX8WLL2gYMZo3JkuXIH2DOpWM+qwA==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.0.0",
        "@istanbuljs/load-nyc-config": "^1.0.0",
        "@istanbuljs/schema": "^0.1.2",
        "istanbul-lib-instrument": "^5.0.4",
        "test-exclude": "^6.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/babel-plugin-polyfill-corejs2": {
      "version": "0.3.1",
      "resolved": "https://registry.npmjs.org/babel-plugin-polyfill-corejs2/-/babel-plugin-polyfill-corejs2-0.3.1.tgz",
      "integrity": "sha512-v7/T6EQcNfVLfcN2X8Lulb7DjprieyLWJK/zOWH5DUYcAgex9sP3h25Q+DLsX9TloXe3y1O8l2q2Jv9q8UVB9w==",
      "dev": true,
      "dependencies": {
        "@babel/compat-data": "^7.13.11",
        "@babel/helper-define-polyfill-provider": "^0.3.1",
        "semver": "^6.1.1"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/babel-plugin-polyfill-corejs2/node_modules/semver": {
      "version": "6.3.0",
      "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.0.tgz",
      "integrity": "sha512-b39TBaTSfV6yBrapU89p5fKekE2m/NwnDocOVruQFS1/veMgdzuPcnOM34M6CwxW8jH/lxEa5rBoDeUwu5HHTw==",
      "dev": true,
      "bin": {
        "semver": "bin/semver.js"
      }
    },
    "node_modules/babel-plugin-polyfill-corejs3": {
      "version": "0.4.0",
      "resolved": "https://registry.npmjs.org/babel-plugin-polyfill-corejs3/-/babel-plugin-polyfill-corejs3-0.4.0.tgz",
      "integrity": "sha512-YxFreYwUfglYKdLUGvIF2nJEsGwj+RhWSX/ije3D2vQPOXuyMLMtg/cCGMDpOA7Nd+MwlNdnGODbd2EwUZPlsw==",
      "dev": true,
      "dependencies": {
        "@babel/helper-define-polyfill-provider": "^0.3.0",
        "core-js-compat": "^3.18.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/babel-plugin-polyfill-regenerator": {
      "version": "0.3.1",
      "resolved": "https://registry.npmjs.org/babel-plugin-polyfill-regenerator/-/babel-plugin-polyfill-regenerator-0.3.1.tgz",
      "integrity": "sha512-Y2B06tvgHYt1x0yz17jGkGeeMr5FeKUu+ASJ+N6nB5lQ8Dapfg42i0OVrf8PNGJ3zKL4A23snMi1IRwrqqND7A==",
      "dev": true,
      "dependencies": {
        "@babel/helper-define-polyfill-provider": "^0.3.1"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/balanced-match": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/balanced-match/-/balanced-match-1.0.2.tgz",
      "integrity": "sha512-3oSeUO0TMV67hN1AmbXsK4yaqU7tjiHlbxRDZOpH0KW9+CeX4bRAaX0Anxt0tx2MrpRpWwQaPwIlISEJhYU5Pw==",
      "dev": true
    },
    "node_modules/base64-js": {
      "version": "1.5.1",
      "resolved": "https://registry.npmjs.org/base64-js/-/base64-js-1.5.1.tgz",
      "integrity": "sha512-AKpaYlHn8t4SVbOHCy+b5+KKgvR4vrsD8vbvrbiQJps7fKDTkjkDry6ji0rUJjC0kzbNePLwzxq8iypo41qeWA==",
      "dev": true,
      "funding": [
        {
          "type": "github",
          "url": "https://github.com/sponsors/feross"
        },
        {
          "type": "patreon",
          "url": "https://www.patreon.com/feross"
        },
        {
          "type": "consulting",
          "url": "https://feross.org/support"
        }
      ]
    },
    "node_modules/base64id": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/base64id/-/base64id-2.0.0.tgz",
      "integrity": "sha512-lGe34o6EHj9y3Kts9R4ZYs/Gr+6N7MCaMlIFA3F1R2O5/m7K06AxfSeO5530PEERE6/WyEg3lsuyw4GHlPZHog==",
      "dev": true,
      "engines": {
        "node": "^4.5.0 || >= 5.9"
      }
    },
    "node_modules/basic-auth": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/basic-auth/-/basic-auth-2.0.1.tgz",
      "integrity": "sha512-NF+epuEdnUYVlGuhaxbbq+dvJttwLnGY+YixlXlME5KpQ5W3CnXA5cVTneY3SPbPDRkcjMbifrwmFYcClgOZeg==",
      "dependencies": {
        "safe-buffer": "5.1.2"
      },
      "engines": {
        "node": ">= 0.8"
      }
    },
    "node_modules/batch": {
      "version": "0.6.1",
      "resolved": "https://registry.npmjs.org/batch/-/batch-0.6.1.tgz",
      "integrity": "sha1-3DQxT05nkxgJP8dgJyUl+UvyXBY=",
      "dev": true
    },
    "node_modules/big.js": {
      "version": "5.2.2",
      "resolved": "https://registry.npmjs.org/big.js/-/big.js-5.2.2.tgz",
      "integrity": "sha512-vyL2OymJxmarO8gxMr0mhChsO9QGwhynfuu4+MHTAW6czfq9humCB7rKpUjDd9YUiDPU4mzpyupFSvOClAwbmQ==",
      "dev": true,
      "engines": {
        "node": "*"
      }
    },
    "node_modules/binary-extensions": {
      "version": "2.2.0",
      "resolved": "https://registry.npmjs.org/binary-extensions/-/binary-extensions-2.2.0.tgz",
      "integrity": "sha512-jDctJ/IVQbZoJykoeHbhXpOlNBqGNcwXJKJog42E5HDPUwQTSdjCHdihjj0DlnheQ7blbT6dHOafNAiS8ooQKA==",
      "dev": true,
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/bl": {
      "version": "4.1.0",
      "resolved": "https://registry.npmjs.org/bl/-/bl-4.1.0.tgz",
      "integrity": "sha512-1W07cM9gS6DcLperZfFSj+bWLtaPGSOHWhPiGzXmvVJbRLdG82sH/Kn8EtW1VqWVA54AKf2h5k5BbnIbwF3h6w==",
      "dev": true,
      "dependencies": {
        "buffer": "^5.5.0",
        "inherits": "^2.0.4",
        "readable-stream": "^3.4.0"
      }
    },
    "node_modules/body-parser": {
      "version": "1.19.1",
      "resolved": "https://registry.npmjs.org/body-parser/-/body-parser-1.19.1.tgz",
      "integrity": "sha512-8ljfQi5eBk8EJfECMrgqNGWPEY5jWP+1IzkzkGdFFEwFQZZyaZ21UqdaHktgiMlH0xLHqIFtE/u2OYE5dOtViA==",
      "dependencies": {
        "bytes": "3.1.1",
        "content-type": "~1.0.4",
        "debug": "2.6.9",
        "depd": "~1.1.2",
        "http-errors": "1.8.1",
        "iconv-lite": "0.4.24",
        "on-finished": "~2.3.0",
        "qs": "6.9.6",
        "raw-body": "2.4.2",
        "type-is": "~1.6.18"
      },
      "engines": {
        "node": ">= 0.8"
      }
    },
    "node_modules/body-parser/node_modules/debug": {
      "version": "2.6.9",
      "resolved": "https://registry.npmjs.org/debug/-/debug-2.6.9.tgz",
      "integrity": "sha512-bC7ElrdJaJnPbAP+1EotYvqZsb3ecl5wi6Bfi6BJTUcNowp6cvspg0jXznRTKDjm/E7AdgFBVeAPVMNcKGsHMA==",
      "dependencies": {
        "ms": "2.0.0"
      }
    },
    "node_modules/body-parser/node_modules/ms": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/ms/-/ms-2.0.0.tgz",
      "integrity": "sha1-VgiurfwAvmwpAd9fmGF4jeDVl8g="
    },
    "node_modules/bonjour": {
      "version": "3.5.0",
      "resolved": "https://registry.npmjs.org/bonjour/-/bonjour-3.5.0.tgz",
      "integrity": "sha1-jokKGD2O6aI5OzhExpGkK897yfU=",
      "dev": true,
      "dependencies": {
        "array-flatten": "^2.1.0",
        "deep-equal": "^1.0.1",
        "dns-equal": "^1.0.0",
        "dns-txt": "^2.0.2",
        "multicast-dns": "^6.0.1",
        "multicast-dns-service-types": "^1.1.0"
      }
    },
    "node_modules/boolbase": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/boolbase/-/boolbase-1.0.0.tgz",
      "integrity": "sha1-aN/1++YMUes3cl6p4+0xDcwed24=",
      "dev": true
    },
    "node_modules/bootstrap": {
      "version": "5.1.3",
      "resolved": "https://registry.npmjs.org/bootstrap/-/bootstrap-5.1.3.tgz",
      "integrity": "sha512-fcQztozJ8jToQWXxVuEyXWW+dSo8AiXWKwiSSrKWsRB/Qt+Ewwza+JWoLKiTuQLaEPhdNAJ7+Dosc9DOIqNy7Q==",
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/bootstrap"
      },
      "peerDependencies": {
        "@popperjs/core": "^2.10.2"
      }
    },
    "node_modules/boxen": {
      "version": "5.1.2",
      "resolved": "https://registry.npmjs.org/boxen/-/boxen-5.1.2.tgz",
      "integrity": "sha512-9gYgQKXx+1nP8mP7CzFyaUARhg7D3n1dF/FnErWmu9l6JvGpNUN278h0aSb+QjoiKSWG+iZ3uHrcqk0qrY9RQQ==",
      "dependencies": {
        "ansi-align": "^3.0.0",
        "camelcase": "^6.2.0",
        "chalk": "^4.1.0",
        "cli-boxes": "^2.2.1",
        "string-width": "^4.2.2",
        "type-fest": "^0.20.2",
        "widest-line": "^3.1.0",
        "wrap-ansi": "^7.0.0"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/boxen/node_modules/ansi-styles": {
      "version": "4.3.0",
      "resolved": "https://registry.npmjs.org/ansi-styles/-/ansi-styles-4.3.0.tgz",
      "integrity": "sha512-zbB9rCJAT1rbjiVDb2hqKFHNYLxgtk8NURxZ3IZwD3F6NtxbXZQCnnSi1Lkx+IDohdPlFp222wVALIheZJQSEg==",
      "dependencies": {
        "color-convert": "^2.0.1"
      },
      "engines": {
        "node": ">=8"
      },
      "funding": {
        "url": "https://github.com/chalk/ansi-styles?sponsor=1"
      }
    },
    "node_modules/boxen/node_modules/camelcase": {
      "version": "6.3.0",
      "resolved": "https://registry.npmjs.org/camelcase/-/camelcase-6.3.0.tgz",
      "integrity": "sha512-Gmy6FhYlCY7uOElZUSbxo2UCDH8owEk996gkbrpsgGtrJLM3J7jGxl9Ic7Qwwj4ivOE5AWZWRMecDdF7hqGjFA==",
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/boxen/node_modules/chalk": {
      "version": "4.1.2",
      "resolved": "https://registry.npmjs.org/chalk/-/chalk-4.1.2.tgz",
      "integrity": "sha512-oKnbhFyRIXpUuez8iBMmyEa4nbj4IOQyuhc/wy9kY7/WVPcwIO9VA668Pu8RkO7+0G76SLROeyw9CpQ061i4mA==",
      "dependencies": {
        "ansi-styles": "^4.1.0",
        "supports-color": "^7.1.0"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/chalk/chalk?sponsor=1"
      }
    },
    "node_modules/boxen/node_modules/color-convert": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/color-convert/-/color-convert-2.0.1.tgz",
      "integrity": "sha512-RRECPsj7iu/xb5oKYcsFHSppFNnsj/52OVTRKb4zP5onXwVF3zVmmToNcOfGC+CRDpfK/U584fMg38ZHCaElKQ==",
      "dependencies": {
        "color-name": "~1.1.4"
      },
      "engines": {
        "node": ">=7.0.0"
      }
    },
    "node_modules/boxen/node_modules/color-name": {
      "version": "1.1.4",
      "resolved": "https://registry.npmjs.org/color-name/-/color-name-1.1.4.tgz",
      "integrity": "sha512-dOy+3AuW3a2wNbZHIuMZpTcgjGuLU/uBL/ubcZF9OXbDo8ff4O8yVp5Bf0efS8uEoYo5q4Fx7dY9OgQGXgAsQA=="
    },
    "node_modules/boxen/node_modules/has-flag": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/has-flag/-/has-flag-4.0.0.tgz",
      "integrity": "sha512-EykJT/Q1KjTWctppgIAgfSO0tKVuZUjhgMr17kqTumMl6Afv3EISleU7qZUzoXDFTAHTDC4NOoG/ZxU3EvlMPQ==",
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/boxen/node_modules/supports-color": {
      "version": "7.2.0",
      "resolved": "https://registry.npmjs.org/supports-color/-/supports-color-7.2.0.tgz",
      "integrity": "sha512-qpCAvRl9stuOHveKsn7HncJRvv501qIacKzQlO/+Lwxc9+0q2wLyv4Dfvt80/DPn2pqOBsJdDiogXGR9+OvwRw==",
      "dependencies": {
        "has-flag": "^4.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/boxen/node_modules/type-fest": {
      "version": "0.20.2",
      "resolved": "https://registry.npmjs.org/type-fest/-/type-fest-0.20.2.tgz",
      "integrity": "sha512-Ne+eE4r0/iWnpAxD852z3A+N0Bt5RN//NjJwRd2VFHEmrywxf5vsZlh4R6lixl6B+wz/8d+maTSAkN1FIkI3LQ==",
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/brace-expansion": {
      "version": "1.1.11",
      "resolved": "https://registry.npmjs.org/brace-expansion/-/brace-expansion-1.1.11.tgz",
      "integrity": "sha512-iCuPHDFgrHX7H2vEI/5xpz07zSHB00TpugqhmYtVmMO6518mCuRMoOYFldEBl0g187ufozdaHgWKcYFb61qGiA==",
      "dev": true,
      "dependencies": {
        "balanced-match": "^1.0.0",
        "concat-map": "0.0.1"
      }
    },
    "node_modules/braces": {
      "version": "3.0.2",
      "resolved": "https://registry.npmjs.org/braces/-/braces-3.0.2.tgz",
      "integrity": "sha512-b8um+L1RzM3WDSzvhm6gIz1yfTbBt6YTlcEKAvsmqCZZFw46z626lVj9j1yEPW33H5H+lBQpZMP1k8l+78Ha0A==",
      "dev": true,
      "dependencies": {
        "fill-range": "^7.0.1"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/browserslist": {
      "version": "4.19.1",
      "resolved": "https://registry.npmjs.org/browserslist/-/browserslist-4.19.1.tgz",
      "integrity": "sha512-u2tbbG5PdKRTUoctO3NBD8FQ5HdPh1ZXPHzp1rwaa5jTc+RV9/+RlWiAIKmjRPQF+xbGM9Kklj5bZQFa2s/38A==",
      "dev": true,
      "dependencies": {
        "caniuse-lite": "^1.0.30001286",
        "electron-to-chromium": "^1.4.17",
        "escalade": "^3.1.1",
        "node-releases": "^2.0.1",
        "picocolors": "^1.0.0"
      },
      "bin": {
        "browserslist": "cli.js"
      },
      "engines": {
        "node": "^6 || ^7 || ^8 || ^9 || ^10 || ^11 || ^12 || >=13.7"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/browserslist"
      }
    },
    "node_modules/buffer": {
      "version": "5.7.1",
      "resolved": "https://registry.npmjs.org/buffer/-/buffer-5.7.1.tgz",
      "integrity": "sha512-EHcyIPBQ4BSGlvjB16k5KgAJ27CIsHY/2JBmCRReo48y9rQ3MaUzWX3KVlBa4U7MyX02HdVj0K7C3WaB3ju7FQ==",
      "dev": true,
      "funding": [
        {
          "type": "github",
          "url": "https://github.com/sponsors/feross"
        },
        {
          "type": "patreon",
          "url": "https://www.patreon.com/feross"
        },
        {
          "type": "consulting",
          "url": "https://feross.org/support"
        }
      ],
      "dependencies": {
        "base64-js": "^1.3.1",
        "ieee754": "^1.1.13"
      }
    },
    "node_modules/buffer-from": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/buffer-from/-/buffer-from-1.1.2.tgz",
      "integrity": "sha512-E+XQCRwSbaaiChtv6k6Dwgc+bx+Bs6vuKJHHl5kox/BaKbhiXzqQOwK4cO22yElGp2OCmjwVhT3HmxgyPGnJfQ==",
      "dev": true
    },
    "node_modules/buffer-indexof": {
      "version": "1.1.1",
      "resolved": "https://registry.npmjs.org/buffer-indexof/-/buffer-indexof-1.1.1.tgz",
      "integrity": "sha512-4/rOEg86jivtPTeOUUT61jJO1Ya1TrR/OkqCSZDyq84WJh3LuuiphBYJN+fm5xufIk4XAFcEwte/8WzC8If/1g==",
      "dev": true
    },
    "node_modules/builtins": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/builtins/-/builtins-1.0.3.tgz",
      "integrity": "sha1-y5T662HIaWRR2zZTThQi+U8K7og=",
      "dev": true
    },
    "node_modules/bytes": {
      "version": "3.1.1",
      "resolved": "https://registry.npmjs.org/bytes/-/bytes-3.1.1.tgz",
      "integrity": "sha512-dWe4nWO/ruEOY7HkUJ5gFt1DCFV9zPRoJr8pV0/ASQermOZjtq8jMjOprC0Kd10GLN+l7xaUPvxzJFWtxGu8Fg==",
      "engines": {
        "node": ">= 0.8"
      }
    },
    "node_modules/cacache": {
      "version": "15.3.0",
      "resolved": "https://registry.npmjs.org/cacache/-/cacache-15.3.0.tgz",
      "integrity": "sha512-VVdYzXEn+cnbXpFgWs5hTT7OScegHVmLhJIR8Ufqk3iFD6A6j5iSX1KuBTfNEv4tdJWE2PzA6IVFtcLC7fN9wQ==",
      "dev": true,
      "dependencies": {
        "@npmcli/fs": "^1.0.0",
        "@npmcli/move-file": "^1.0.1",
        "chownr": "^2.0.0",
        "fs-minipass": "^2.0.0",
        "glob": "^7.1.4",
        "infer-owner": "^1.0.4",
        "lru-cache": "^6.0.0",
        "minipass": "^3.1.1",
        "minipass-collect": "^1.0.2",
        "minipass-flush": "^1.0.5",
        "minipass-pipeline": "^1.2.2",
        "mkdirp": "^1.0.3",
        "p-map": "^4.0.0",
        "promise-inflight": "^1.0.1",
        "rimraf": "^3.0.2",
        "ssri": "^8.0.1",
        "tar": "^6.0.2",
        "unique-filename": "^1.1.1"
      },
      "engines": {
        "node": ">= 10"
      }
    },
    "node_modules/cacheable-request": {
      "version": "6.1.0",
      "resolved": "https://registry.npmjs.org/cacheable-request/-/cacheable-request-6.1.0.tgz",
      "integrity": "sha512-Oj3cAGPCqOZX7Rz64Uny2GYAZNliQSqfbePrgAQ1wKAihYmCUnraBtJtKcGR4xz7wF+LoJC+ssFZvv5BgF9Igg==",
      "dependencies": {
        "clone-response": "^1.0.2",
        "get-stream": "^5.1.0",
        "http-cache-semantics": "^4.0.0",
        "keyv": "^3.0.0",
        "lowercase-keys": "^2.0.0",
        "normalize-url": "^4.1.0",
        "responselike": "^1.0.2"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/cacheable-request/node_modules/get-stream": {
      "version": "5.2.0",
      "resolved": "https://registry.npmjs.org/get-stream/-/get-stream-5.2.0.tgz",
      "integrity": "sha512-nBF+F1rAZVCu/p7rjzgA+Yb4lfYXrpl7a6VmJrU8wF9I1CKvP/QwPNZHnOlwbTkY6dvtFIzFMSyQXbLoTQPRpA==",
      "dependencies": {
        "pump": "^3.0.0"
      },
      "engines": {
        "node": ">=8"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/cacheable-request/node_modules/lowercase-keys": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/lowercase-keys/-/lowercase-keys-2.0.0.tgz",
      "integrity": "sha512-tqNXrS78oMOE73NMxK4EMLQsQowWf8jKooH9g7xPavRT706R6bkQJ6DY2Te7QukaZsulxa30wQ7bk0pm4XiHmA==",
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/call-bind": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/call-bind/-/call-bind-1.0.2.tgz",
      "integrity": "sha512-7O+FbCihrB5WGbFYesctwmTKae6rOiIzmz1icreWJ+0aA7LJfuqhEso2T9ncpcFtzMQtzXf2QGGueWJGTYsqrA==",
      "dev": true,
      "dependencies": {
        "function-bind": "^1.1.1",
        "get-intrinsic": "^1.0.2"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/callsites": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/callsites/-/callsites-3.1.0.tgz",
      "integrity": "sha512-P8BjAsXvZS+VIDUI11hHCQEv74YT67YUi5JJFNWIqL235sBmjX4+qx9Muvls5ivyNENctx46xQLQ3aTuE7ssaQ==",
      "dev": true,
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/camelcase": {
      "version": "5.3.1",
      "resolved": "https://registry.npmjs.org/camelcase/-/camelcase-5.3.1.tgz",
      "integrity": "sha512-L28STB170nwWS63UjtlEOE3dldQApaJXZkOI1uMFfzf3rRuPegHaHesyee+YxQ+W6SvRDQV6UrdOdRiR153wJg==",
      "dev": true,
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/caniuse-lite": {
      "version": "1.0.30001303",
      "resolved": "https://registry.npmjs.org/caniuse-lite/-/caniuse-lite-1.0.30001303.tgz",
      "integrity": "sha512-/Mqc1oESndUNszJP0kx0UaQU9kEv9nNtJ7Kn8AdA0mNnH8eR1cj0kG+NbNuC1Wq/b21eA8prhKRA3bbkjONegQ==",
      "dev": true,
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/browserslist"
      }
    },
    "node_modules/canonical-path": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/canonical-path/-/canonical-path-1.0.0.tgz",
      "integrity": "sha512-feylzsbDxi1gPZ1IjystzIQZagYYLvfKrSuygUCgf7z6x790VEzze5QEkdSV1U58RA7Hi0+v6fv4K54atOzATg==",
      "dev": true
    },
    "node_modules/chalk": {
      "version": "2.4.2",
      "resolved": "https://registry.npmjs.org/chalk/-/chalk-2.4.2.tgz",
      "integrity": "sha512-Mti+f9lpJNcwF4tWV8/OrTTtF1gZi+f8FqlyAdouralcFWFQWF2+NgCHShjkCb+IFBLq9buZwE1xckQU4peSuQ==",
      "dev": true,
      "dependencies": {
        "ansi-styles": "^3.2.1",
        "escape-string-regexp": "^1.0.5",
        "supports-color": "^5.3.0"
      },
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/chardet": {
      "version": "0.7.0",
      "resolved": "https://registry.npmjs.org/chardet/-/chardet-0.7.0.tgz",
      "integrity": "sha512-mT8iDcrh03qDGRRmoA2hmBJnxpllMR+0/0qlzjqZES6NdiWDcZkCNAk4rPFZ9Q85r27unkiNNg8ZOiwZXBHwcA==",
      "dev": true
    },
    "node_modules/chokidar": {
      "version": "3.5.3",
      "resolved": "https://registry.npmjs.org/chokidar/-/chokidar-3.5.3.tgz",
      "integrity": "sha512-Dr3sfKRP6oTcjf2JmUmFJfeVMvXBdegxB0iVQ5eb2V10uFJUCAS8OByZdVAyVb8xXNz3GjjTgj9kLWsZTqE6kw==",
      "dev": true,
      "funding": [
        {
          "type": "individual",
          "url": "https://paulmillr.com/funding/"
        }
      ],
      "dependencies": {
        "anymatch": "~3.1.2",
        "braces": "~3.0.2",
        "glob-parent": "~5.1.2",
        "is-binary-path": "~2.1.0",
        "is-glob": "~4.0.1",
        "normalize-path": "~3.0.0",
        "readdirp": "~3.6.0"
      },
      "engines": {
        "node": ">= 8.10.0"
      },
      "optionalDependencies": {
        "fsevents": "~2.3.2"
      }
    },
    "node_modules/chownr": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/chownr/-/chownr-2.0.0.tgz",
      "integrity": "sha512-bIomtDF5KGpdogkLd9VspvFzk9KfpyyGlS8YFVZl7TGPBHL5snIOnxeshwVgPteQ9b4Eydl+pVbIyE1DcvCWgQ==",
      "dev": true,
      "engines": {
        "node": ">=10"
      }
    },
    "node_modules/chrome-trace-event": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/chrome-trace-event/-/chrome-trace-event-1.0.3.tgz",
      "integrity": "sha512-p3KULyQg4S7NIHixdwbGX+nFHkoBiA4YQmyWtjb8XngSKV124nJmRysgAeujbUVb15vh+RvFUfCPqU7rXk+hZg==",
      "dev": true,
      "engines": {
        "node": ">=6.0"
      }
    },
    "node_modules/ci-info": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/ci-info/-/ci-info-2.0.0.tgz",
      "integrity": "sha512-5tK7EtrZ0N+OLFMthtqOj4fI2Jeb88C4CAZPu25LDVUgXJ0A3Js4PMGqrn0JU1W0Mh1/Z8wZzYPxqUrXeBboCQ=="
    },
    "node_modules/circular-dependency-plugin": {
      "version": "5.2.2",
      "resolved": "https://registry.npmjs.org/circular-dependency-plugin/-/circular-dependency-plugin-5.2.2.tgz",
      "integrity": "sha512-g38K9Cm5WRwlaH6g03B9OEz/0qRizI+2I7n+Gz+L5DxXJAPAiWQvwlYNm1V1jkdpUv95bOe/ASm2vfi/G560jQ==",
      "dev": true,
      "engines": {
        "node": ">=6.0.0"
      },
      "peerDependencies": {
        "webpack": ">=4.0.1"
      }
    },
    "node_modules/clean-stack": {
      "version": "2.2.0",
      "resolved": "https://registry.npmjs.org/clean-stack/-/clean-stack-2.2.0.tgz",
      "integrity": "sha512-4diC9HaTE+KRAMWhDhrGOECgWZxoevMc5TlkObMqNSsVU62PYzXZ/SMTjzyGAFF1YusgxGcSWTEXBhp0CPwQ1A==",
      "dev": true,
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/cli-boxes": {
      "version": "2.2.1",
      "resolved": "https://registry.npmjs.org/cli-boxes/-/cli-boxes-2.2.1.tgz",
      "integrity": "sha512-y4coMcylgSCdVinjiDBuR8PCC2bLjyGTwEmPb9NHR/QaNU6EUOXcTY/s6VjGMD6ENSEaeQYHCY0GNGS5jfMwPw==",
      "engines": {
        "node": ">=6"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/cli-cursor": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/cli-cursor/-/cli-cursor-3.1.0.tgz",
      "integrity": "sha512-I/zHAwsKf9FqGoXM4WWRACob9+SNukZTd94DWF57E4toouRulbCxcUh6RKUEOQlYTHJnzkPMySvPNaaSLNfLZw==",
      "dev": true,
      "dependencies": {
        "restore-cursor": "^3.1.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/cli-spinners": {
      "version": "2.6.1",
      "resolved": "https://registry.npmjs.org/cli-spinners/-/cli-spinners-2.6.1.tgz",
      "integrity": "sha512-x/5fWmGMnbKQAaNwN+UZlV79qBLM9JFnJuJ03gIi5whrob0xV0ofNVHy9DhwGdsMJQc2OKv0oGmLzvaqvAVv+g==",
      "dev": true,
      "engines": {
        "node": ">=6"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/cli-width": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/cli-width/-/cli-width-3.0.0.tgz",
      "integrity": "sha512-FxqpkPPwu1HjuN93Omfm4h8uIanXofW0RxVEW3k5RKx+mJJYSthzNhp32Kzxxy3YAEZ/Dc/EWN1vZRY0+kOhbw==",
      "dev": true,
      "engines": {
        "node": ">= 10"
      }
    },
    "node_modules/cliui": {
      "version": "7.0.4",
      "resolved": "https://registry.npmjs.org/cliui/-/cliui-7.0.4.tgz",
      "integrity": "sha512-OcRE68cOsVMXp1Yvonl/fzkQOyjLSu/8bhPDfQt0e0/Eb283TKP20Fs2MqoPsr9SwA595rRCA+QMzYc9nBP+JQ==",
      "dependencies": {
        "string-width": "^4.2.0",
        "strip-ansi": "^6.0.0",
        "wrap-ansi": "^7.0.0"
      }
    },
    "node_modules/clone": {
      "version": "1.0.4",
      "resolved": "https://registry.npmjs.org/clone/-/clone-1.0.4.tgz",
      "integrity": "sha1-2jCcwmPfFZlMaIypAheco8fNfH4=",
      "dev": true,
      "engines": {
        "node": ">=0.8"
      }
    },
    "node_modules/clone-deep": {
      "version": "4.0.1",
      "resolved": "https://registry.npmjs.org/clone-deep/-/clone-deep-4.0.1.tgz",
      "integrity": "sha512-neHB9xuzh/wk0dIHweyAXv2aPGZIVk3pLMe+/RNzINf17fe0OG96QroktYAUm7SM1PBnzTabaLboqqxDyMU+SQ==",
      "dev": true,
      "dependencies": {
        "is-plain-object": "^2.0.4",
        "kind-of": "^6.0.2",
        "shallow-clone": "^3.0.0"
      },
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/clone-response": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/clone-response/-/clone-response-1.0.2.tgz",
      "integrity": "sha1-0dyXOSAxTfZ/vrlCI7TuNQI56Ws=",
      "dependencies": {
        "mimic-response": "^1.0.0"
      }
    },
    "node_modules/color-convert": {
      "version": "1.9.3",
      "resolved": "https://registry.npmjs.org/color-convert/-/color-convert-1.9.3.tgz",
      "integrity": "sha512-QfAUtd+vFdAtFQcC8CCyYt1fYWxSqAiK2cSD6zDB8N3cpsEBAvRxp9zOGg6G/SHHJYAT88/az/IuDGALsNVbGg==",
      "dev": true,
      "dependencies": {
        "color-name": "1.1.3"
      }
    },
    "node_modules/color-name": {
      "version": "1.1.3",
      "resolved": "https://registry.npmjs.org/color-name/-/color-name-1.1.3.tgz",
      "integrity": "sha1-p9BVi9icQveV3UIyj3QIMcpTvCU=",
      "dev": true
    },
    "node_modules/color-support": {
      "version": "1.1.3",
      "resolved": "https://registry.npmjs.org/color-support/-/color-support-1.1.3.tgz",
      "integrity": "sha512-qiBjkpbMLO/HL68y+lh4q0/O1MZFj2RX6X/KmMa3+gJD3z+WwI1ZzDHysvqHGS3mP6mznPckpXmw1nI9cJjyRg==",
      "dev": true,
      "bin": {
        "color-support": "bin.js"
      }
    },
    "node_modules/colorette": {
      "version": "2.0.16",
      "resolved": "https://registry.npmjs.org/colorette/-/colorette-2.0.16.tgz",
      "integrity": "sha512-hUewv7oMjCp+wkBv5Rm0v87eJhq4woh5rSR+42YSQJKecCqgIqNkZ6lAlQms/BwHPJA5NKMRlpxPRv0n8HQW6g==",
      "dev": true
    },
    "node_modules/colors": {
      "version": "1.4.0",
      "resolved": "https://registry.npmjs.org/colors/-/colors-1.4.0.tgz",
      "integrity": "sha512-a+UqTh4kgZg/SlGvfbzDHpgRu7AAQOmmqRHJnxhRZICKFUT91brVhNNt58CMWU9PsBbv3PDCZUHbVxuDiH2mtA==",
      "dev": true,
      "engines": {
        "node": ">=0.1.90"
      }
    },
    "node_modules/commander": {
      "version": "2.20.3",
      "resolved": "https://registry.npmjs.org/commander/-/commander-2.20.3.tgz",
      "integrity": "sha512-GpVkmM8vF2vQUkj2LvZmD35JxeJOLCwJ9cUkugyk2nuhbv3+mJvpLYYt+0+USMxE+oj+ey/lJEnhZw75x/OMcQ==",
      "dev": true
    },
    "node_modules/commondir": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/commondir/-/commondir-1.0.1.tgz",
      "integrity": "sha1-3dgA2gxmEnOTzKWVDqloo6rxJTs=",
      "dev": true
    },
    "node_modules/component-emitter": {
      "version": "1.3.0",
      "resolved": "https://registry.npmjs.org/component-emitter/-/component-emitter-1.3.0.tgz",
      "integrity": "sha512-Rd3se6QB+sO1TwqZjscQrurpEPIfO0/yYnSin6Q/rD3mOutHvUrCAhJub3r90uNb+SESBuE0QYoB90YdfatsRg==",
      "dev": true
    },
    "node_modules/compressible": {
      "version": "2.0.18",
      "resolved": "https://registry.npmjs.org/compressible/-/compressible-2.0.18.tgz",
      "integrity": "sha512-AF3r7P5dWxL8MxyITRMlORQNaOA2IkAFaTr4k7BUumjPtRpGDTZpl0Pb1XCO6JeDCBdp126Cgs9sMxqSjgYyRg==",
      "dependencies": {
        "mime-db": ">= 1.43.0 < 2"
      },
      "engines": {
        "node": ">= 0.6"
      }
    },
    "node_modules/compression": {
      "version": "1.7.4",
      "resolved": "https://registry.npmjs.org/compression/-/compression-1.7.4.tgz",
      "integrity": "sha512-jaSIDzP9pZVS4ZfQ+TzvtiWhdpFhE2RDHz8QJkpX9SIpLq88VueF5jJw6t+6CUQcAoA6t+x89MLrWAqpfDE8iQ==",
      "dependencies": {
        "accepts": "~1.3.5",
        "bytes": "3.0.0",
        "compressible": "~2.0.16",
        "debug": "2.6.9",
        "on-headers": "~1.0.2",
        "safe-buffer": "5.1.2",
        "vary": "~1.1.2"
      },
      "engines": {
        "node": ">= 0.8.0"
      }
    },
    "node_modules/compression/node_modules/bytes": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/bytes/-/bytes-3.0.0.tgz",
      "integrity": "sha1-0ygVQE1olpn4Wk6k+odV3ROpYEg=",
      "engines": {
        "node": ">= 0.8"
      }
    },
    "node_modules/compression/node_modules/debug": {
      "version": "2.6.9",
      "resolved": "https://registry.npmjs.org/debug/-/debug-2.6.9.tgz",
      "integrity": "sha512-bC7ElrdJaJnPbAP+1EotYvqZsb3ecl5wi6Bfi6BJTUcNowp6cvspg0jXznRTKDjm/E7AdgFBVeAPVMNcKGsHMA==",
      "dependencies": {
        "ms": "2.0.0"
      }
    },
    "node_modules/compression/node_modules/ms": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/ms/-/ms-2.0.0.tgz",
      "integrity": "sha1-VgiurfwAvmwpAd9fmGF4jeDVl8g="
    },
    "node_modules/concat-map": {
      "version": "0.0.1",
      "resolved": "https://registry.npmjs.org/concat-map/-/concat-map-0.0.1.tgz",
      "integrity": "sha1-2Klr13/Wjfd5OnMDajug1UBdR3s=",
      "dev": true
    },
    "node_modules/configstore": {
      "version": "5.0.1",
      "resolved": "https://registry.npmjs.org/configstore/-/configstore-5.0.1.tgz",
      "integrity": "sha512-aMKprgk5YhBNyH25hj8wGt2+D52Sw1DRRIzqBwLp2Ya9mFmY8KPvvtvmna8SxVR9JMZ4kzMD68N22vlaRpkeFA==",
      "dependencies": {
        "dot-prop": "^5.2.0",
        "graceful-fs": "^4.1.2",
        "make-dir": "^3.0.0",
        "unique-string": "^2.0.0",
        "write-file-atomic": "^3.0.0",
        "xdg-basedir": "^4.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/connect": {
      "version": "3.7.0",
      "resolved": "https://registry.npmjs.org/connect/-/connect-3.7.0.tgz",
      "integrity": "sha512-ZqRXc+tZukToSNmh5C2iWMSoV3X1YUcPbqEM4DkEG5tNQXrQUZCNVGGv3IuicnkMtPfGf3Xtp8WCXs295iQ1pQ==",
      "dev": true,
      "dependencies": {
        "debug": "2.6.9",
        "finalhandler": "1.1.2",
        "parseurl": "~1.3.3",
        "utils-merge": "1.0.1"
      },
      "engines": {
        "node": ">= 0.10.0"
      }
    },
    "node_modules/connect-history-api-fallback": {
      "version": "1.6.0",
      "resolved": "https://registry.npmjs.org/connect-history-api-fallback/-/connect-history-api-fallback-1.6.0.tgz",
      "integrity": "sha512-e54B99q/OUoH64zYYRf3HBP5z24G38h5D3qXu23JGRoigpX5Ss4r9ZnDk3g0Z8uQC2x2lPaJ+UlWBc1ZWBWdLg==",
      "dev": true,
      "engines": {
        "node": ">=0.8"
      }
    },
    "node_modules/connect-pause": {
      "version": "0.1.1",
      "resolved": "https://registry.npmjs.org/connect-pause/-/connect-pause-0.1.1.tgz",
      "integrity": "sha1-smmyu4Ldsaw9tQmcD7WCq6mfs3o=",
      "engines": {
        "node": "*"
      }
    },
    "node_modules/connect/node_modules/debug": {
      "version": "2.6.9",
      "resolved": "https://registry.npmjs.org/debug/-/debug-2.6.9.tgz",
      "integrity": "sha512-bC7ElrdJaJnPbAP+1EotYvqZsb3ecl5wi6Bfi6BJTUcNowp6cvspg0jXznRTKDjm/E7AdgFBVeAPVMNcKGsHMA==",
      "dev": true,
      "dependencies": {
        "ms": "2.0.0"
      }
    },
    "node_modules/connect/node_modules/ms": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/ms/-/ms-2.0.0.tgz",
      "integrity": "sha1-VgiurfwAvmwpAd9fmGF4jeDVl8g=",
      "dev": true
    },
    "node_modules/console-control-strings": {
      "version": "1.1.0",
      "resolved": "https://registry.npmjs.org/console-control-strings/-/console-control-strings-1.1.0.tgz",
      "integrity": "sha1-PXz0Rk22RG6mRL9LOVB/mFEAjo4=",
      "dev": true
    },
    "node_modules/content-disposition": {
      "version": "0.5.4",
      "resolved": "https://registry.npmjs.org/content-disposition/-/content-disposition-0.5.4.tgz",
      "integrity": "sha512-FveZTNuGw04cxlAiWbzi6zTAL/lhehaWbTtgluJh4/E95DqMwTmha3KZN1aAWA8cFIhHzMZUvLevkw5Rqk+tSQ==",
      "dependencies": {
        "safe-buffer": "5.2.1"
      },
      "engines": {
        "node": ">= 0.6"
      }
    },
    "node_modules/content-disposition/node_modules/safe-buffer": {
      "version": "5.2.1",
      "resolved": "https://registry.npmjs.org/safe-buffer/-/safe-buffer-5.2.1.tgz",
      "integrity": "sha512-rp3So07KcdmmKbGvgaNxQSJr7bGVSVk5S9Eq1F+ppbRo70+YeaDxkw5Dd8NPN+GD6bjnYm2VuPuCXmpuYvmCXQ==",
      "funding": [
        {
          "type": "github",
          "url": "https://github.com/sponsors/feross"
        },
        {
          "type": "patreon",
          "url": "https://www.patreon.com/feross"
        },
        {
          "type": "consulting",
          "url": "https://feross.org/support"
        }
      ]
    },
    "node_modules/content-type": {
      "version": "1.0.4",
      "resolved": "https://registry.npmjs.org/content-type/-/content-type-1.0.4.tgz",
      "integrity": "sha512-hIP3EEPs8tB9AT1L+NUqtwOAps4mk2Zob89MWXMHjHWg9milF/j4osnnQLXBCBFBk/tvIG/tUc9mOUJiPBhPXA==",
      "engines": {
        "node": ">= 0.6"
      }
    },
    "node_modules/convert-source-map": {
      "version": "1.8.0",
      "resolved": "https://registry.npmjs.org/convert-source-map/-/convert-source-map-1.8.0.tgz",
      "integrity": "sha512-+OQdjP49zViI/6i7nIJpA8rAl4sV/JdPfU9nZs3VqOwGIgizICvuN2ru6fMd+4llL0tar18UYJXfZ/TWtmhUjA==",
      "dev": true,
      "dependencies": {
        "safe-buffer": "~5.1.1"
      }
    },
    "node_modules/cookie": {
      "version": "0.4.1",
      "resolved": "https://registry.npmjs.org/cookie/-/cookie-0.4.1.tgz",
      "integrity": "sha512-ZwrFkGJxUR3EIoXtO+yVE69Eb7KlixbaeAWfBQB9vVsNn/o+Yw69gBWSSDK825hQNdN+wF8zELf3dFNl/kxkUA==",
      "engines": {
        "node": ">= 0.6"
      }
    },
    "node_modules/cookie-signature": {
      "version": "1.0.6",
      "resolved": "https://registry.npmjs.org/cookie-signature/-/cookie-signature-1.0.6.tgz",
      "integrity": "sha1-4wOogrNCzD7oylE6eZmXNNqzriw="
    },
    "node_modules/copy-anything": {
      "version": "2.0.6",
      "resolved": "https://registry.npmjs.org/copy-anything/-/copy-anything-2.0.6.tgz",
      "integrity": "sha512-1j20GZTsvKNkc4BY3NpMOM8tt///wY3FpIzozTOFO2ffuZcV61nojHXVKIy3WM+7ADCy5FVhdZYHYDdgTU0yJw==",
      "dev": true,
      "dependencies": {
        "is-what": "^3.14.1"
      },
      "funding": {
        "url": "https://github.com/sponsors/mesqueeb"
      }
    },
    "node_modules/copy-webpack-plugin": {
      "version": "10.0.0",
      "resolved": "https://registry.npmjs.org/copy-webpack-plugin/-/copy-webpack-plugin-10.0.0.tgz",
      "integrity": "sha512-tuCVuFMBbRsb7IH0q1CUb50/Skv+7a6c7DJ+xi4fAbOzNLTYVMUTPnf8uGvKPtmqTvzYBrfEFo7YgP4TsUWmtg==",
      "dev": true,
      "dependencies": {
        "fast-glob": "^3.2.7",
        "glob-parent": "^6.0.1",
        "globby": "^12.0.2",
        "normalize-path": "^3.0.0",
        "schema-utils": "^4.0.0",
        "serialize-javascript": "^6.0.0"
      },
      "engines": {
        "node": ">= 12.20.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/webpack"
      },
      "peerDependencies": {
        "webpack": "^5.1.0"
      }
    },
    "node_modules/copy-webpack-plugin/node_modules/glob-parent": {
      "version": "6.0.2",
      "resolved": "https://registry.npmjs.org/glob-parent/-/glob-parent-6.0.2.tgz",
      "integrity": "sha512-XxwI8EOhVQgWp6iDL+3b0r86f4d6AX6zSU55HfB4ydCEuXLXc5FcYeOu+nnGftS4TEju/11rt4KJPTMgbfmv4A==",
      "dev": true,
      "dependencies": {
        "is-glob": "^4.0.3"
      },
      "engines": {
        "node": ">=10.13.0"
      }
    },
    "node_modules/copy-webpack-plugin/node_modules/schema-utils": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/schema-utils/-/schema-utils-4.0.0.tgz",
      "integrity": "sha512-1edyXKgh6XnJsJSQ8mKWXnN/BVaIbFMLpouRUrXgVq7WYne5kw3MW7UPhO44uRXQSIpTSXoJbmrR2X0w9kUTyg==",
      "dev": true,
      "dependencies": {
        "@types/json-schema": "^7.0.9",
        "ajv": "^8.8.0",
        "ajv-formats": "^2.1.1",
        "ajv-keywords": "^5.0.0"
      },
      "engines": {
        "node": ">= 12.13.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/webpack"
      }
    },
    "node_modules/core-js": {
      "version": "3.19.3",
      "resolved": "https://registry.npmjs.org/core-js/-/core-js-3.19.3.tgz",
      "integrity": "sha512-LeLBMgEGSsG7giquSzvgBrTS7V5UL6ks3eQlUSbN8dJStlLFiRzUm5iqsRyzUB8carhfKjkJ2vzKqE6z1Vga9g==",
      "dev": true,
      "hasInstallScript": true,
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/core-js"
      }
    },
    "node_modules/core-js-compat": {
      "version": "3.20.3",
      "resolved": "https://registry.npmjs.org/core-js-compat/-/core-js-compat-3.20.3.tgz",
      "integrity": "sha512-c8M5h0IkNZ+I92QhIpuSijOxGAcj3lgpsWdkCqmUTZNwidujF4r3pi6x1DCN+Vcs5qTS2XWWMfWSuCqyupX8gw==",
      "dev": true,
      "dependencies": {
        "browserslist": "^4.19.1",
        "semver": "7.0.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/core-js"
      }
    },
    "node_modules/core-js-compat/node_modules/semver": {
      "version": "7.0.0",
      "resolved": "https://registry.npmjs.org/semver/-/semver-7.0.0.tgz",
      "integrity": "sha512-+GB6zVA9LWh6zovYQLALHwv5rb2PHGlJi3lfiqIHxR0uuwCgefcOJc59v9fv1w8GbStwxuuqqAjI9NMAOOgq1A==",
      "dev": true,
      "bin": {
        "semver": "bin/semver.js"
      }
    },
    "node_modules/core-util-is": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/core-util-is/-/core-util-is-1.0.3.tgz",
      "integrity": "sha512-ZQBvi1DcpJ4GDqanjucZ2Hj3wEO5pZDS89BWbkcrvdxksJorwUDDZamX9ldFkp9aw2lmBDLgkObEA4DWNJ9FYQ==",
      "dev": true
    },
    "node_modules/cors": {
      "version": "2.8.5",
      "resolved": "https://registry.npmjs.org/cors/-/cors-2.8.5.tgz",
      "integrity": "sha512-KIHbLJqu73RGr/hnbrO9uBeixNGuvSQjul/jdFvS/KFSIH1hWVd1ng7zOHx+YrEfInLG7q4n6GHQ9cDtxv/P6g==",
      "dependencies": {
        "object-assign": "^4",
        "vary": "^1"
      },
      "engines": {
        "node": ">= 0.10"
      }
    },
    "node_modules/cosmiconfig": {
      "version": "7.0.1",
      "resolved": "https://registry.npmjs.org/cosmiconfig/-/cosmiconfig-7.0.1.tgz",
      "integrity": "sha512-a1YWNUV2HwGimB7dU2s1wUMurNKjpx60HxBB6xUM8Re+2s1g1IIfJvFR0/iCF+XHdE0GMTKTuLR32UQff4TEyQ==",
      "dev": true,
      "dependencies": {
        "@types/parse-json": "^4.0.0",
        "import-fresh": "^3.2.1",
        "parse-json": "^5.0.0",
        "path-type": "^4.0.0",
        "yaml": "^1.10.0"
      },
      "engines": {
        "node": ">=10"
      }
    },
    "node_modules/critters": {
      "version": "0.0.16",
      "resolved": "https://registry.npmjs.org/critters/-/critters-0.0.16.tgz",
      "integrity": "sha512-JwjgmO6i3y6RWtLYmXwO5jMd+maZt8Tnfu7VVISmEWyQqfLpB8soBswf8/2bu6SBXxtKA68Al3c+qIG1ApT68A==",
      "dev": true,
      "dependencies": {
        "chalk": "^4.1.0",
        "css-select": "^4.2.0",
        "parse5": "^6.0.1",
        "parse5-htmlparser2-tree-adapter": "^6.0.1",
        "postcss": "^8.3.7",
        "pretty-bytes": "^5.3.0"
      }
    },
    "node_modules/critters/node_modules/ansi-styles": {
      "version": "4.3.0",
      "resolved": "https://registry.npmjs.org/ansi-styles/-/ansi-styles-4.3.0.tgz",
      "integrity": "sha512-zbB9rCJAT1rbjiVDb2hqKFHNYLxgtk8NURxZ3IZwD3F6NtxbXZQCnnSi1Lkx+IDohdPlFp222wVALIheZJQSEg==",
      "dev": true,
      "dependencies": {
        "color-convert": "^2.0.1"
      },
      "engines": {
        "node": ">=8"
      },
      "funding": {
        "url": "https://github.com/chalk/ansi-styles?sponsor=1"
      }
    },
    "node_modules/critters/node_modules/chalk": {
      "version": "4.1.2",
      "resolved": "https://registry.npmjs.org/chalk/-/chalk-4.1.2.tgz",
      "integrity": "sha512-oKnbhFyRIXpUuez8iBMmyEa4nbj4IOQyuhc/wy9kY7/WVPcwIO9VA668Pu8RkO7+0G76SLROeyw9CpQ061i4mA==",
      "dev": true,
      "dependencies": {
        "ansi-styles": "^4.1.0",
        "supports-color": "^7.1.0"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/chalk/chalk?sponsor=1"
      }
    },
    "node_modules/critters/node_modules/color-convert": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/color-convert/-/color-convert-2.0.1.tgz",
      "integrity": "sha512-RRECPsj7iu/xb5oKYcsFHSppFNnsj/52OVTRKb4zP5onXwVF3zVmmToNcOfGC+CRDpfK/U584fMg38ZHCaElKQ==",
      "dev": true,
      "dependencies": {
        "color-name": "~1.1.4"
      },
      "engines": {
        "node": ">=7.0.0"
      }
    },
    "node_modules/critters/node_modules/color-name": {
      "version": "1.1.4",
      "resolved": "https://registry.npmjs.org/color-name/-/color-name-1.1.4.tgz",
      "integrity": "sha512-dOy+3AuW3a2wNbZHIuMZpTcgjGuLU/uBL/ubcZF9OXbDo8ff4O8yVp5Bf0efS8uEoYo5q4Fx7dY9OgQGXgAsQA==",
      "dev": true
    },
    "node_modules/critters/node_modules/has-flag": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/has-flag/-/has-flag-4.0.0.tgz",
      "integrity": "sha512-EykJT/Q1KjTWctppgIAgfSO0tKVuZUjhgMr17kqTumMl6Afv3EISleU7qZUzoXDFTAHTDC4NOoG/ZxU3EvlMPQ==",
      "dev": true,
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/critters/node_modules/supports-color": {
      "version": "7.2.0",
      "resolved": "https://registry.npmjs.org/supports-color/-/supports-color-7.2.0.tgz",
      "integrity": "sha512-qpCAvRl9stuOHveKsn7HncJRvv501qIacKzQlO/+Lwxc9+0q2wLyv4Dfvt80/DPn2pqOBsJdDiogXGR9+OvwRw==",
      "dev": true,
      "dependencies": {
        "has-flag": "^4.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/cross-spawn": {
      "version": "7.0.3",
      "resolved": "https://registry.npmjs.org/cross-spawn/-/cross-spawn-7.0.3.tgz",
      "integrity": "sha512-iRDPJKUPVEND7dHPO8rkbOnPpyDygcDFtWjpeWNCgy8WP2rXcxXL8TskReQl6OrB2G7+UJrags1q15Fudc7G6w==",
      "dev": true,
      "dependencies": {
        "path-key": "^3.1.0",
        "shebang-command": "^2.0.0",
        "which": "^2.0.1"
      },
      "engines": {
        "node": ">= 8"
      }
    },
    "node_modules/cross-spawn/node_modules/which": {
      "version": "2.0.2",
      "resolved": "https://registry.npmjs.org/which/-/which-2.0.2.tgz",
      "integrity": "sha512-BLI3Tl1TW3Pvl70l3yq3Y64i+awpwXqsGBYWkkqMtnbXgrMD+yj7rhW0kuEDxzJaYXGjEW5ogapKNMEKNMjibA==",
      "dev": true,
      "dependencies": {
        "isexe": "^2.0.0"
      },
      "bin": {
        "node-which": "bin/node-which"
      },
      "engines": {
        "node": ">= 8"
      }
    },
    "node_modules/crypto-random-string": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/crypto-random-string/-/crypto-random-string-2.0.0.tgz",
      "integrity": "sha512-v1plID3y9r/lPhviJ1wrXpLeyUIGAZ2SHNYTEapm7/8A9nLPoyvVp3RK/EPFqn5kEznyWgYZNsRtYYIWbuG8KA==",
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/css": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/css/-/css-3.0.0.tgz",
      "integrity": "sha512-DG9pFfwOrzc+hawpmqX/dHYHJG+Bsdb0klhyi1sDneOgGOXy9wQIC8hzyVp1e4NRYDBdxcylvywPkkXCHAzTyQ==",
      "dev": true,
      "dependencies": {
        "inherits": "^2.0.4",
        "source-map": "^0.6.1",
        "source-map-resolve": "^0.6.0"
      }
    },
    "node_modules/css-blank-pseudo": {
      "version": "3.0.2",
      "resolved": "https://registry.npmjs.org/css-blank-pseudo/-/css-blank-pseudo-3.0.2.tgz",
      "integrity": "sha512-hOb1LFjRR+8ocA071xUSmg5VslJ8NGo/I2qpUpdeAYyBVCgupS5O8SEVo4SxEMYyFBNodBkzG3T1iqW9HCXxew==",
      "dev": true,
      "dependencies": {
        "postcss-selector-parser": "^6.0.8"
      },
      "bin": {
        "css-blank-pseudo": "dist/cli.cjs"
      },
      "engines": {
        "node": "^12 || ^14 || >=16"
      },
      "peerDependencies": {
        "postcss": "^8.3"
      }
    },
    "node_modules/css-has-pseudo": {
      "version": "3.0.3",
      "resolved": "https://registry.npmjs.org/css-has-pseudo/-/css-has-pseudo-3.0.3.tgz",
      "integrity": "sha512-0gDYWEKaGacwxCqvQ3Ypg6wGdD1AztbMm5h1JsactG2hP2eiflj808QITmuWBpE7sjSEVrAlZhPTVd/nNMj/hQ==",
      "dev": true,
      "dependencies": {
        "postcss-selector-parser": "^6.0.8"
      },
      "bin": {
        "css-has-pseudo": "dist/cli.cjs"
      },
      "engines": {
        "node": "^12 || ^14 || >=16"
      },
      "peerDependencies": {
        "postcss": "^8.3"
      }
    },
    "node_modules/css-loader": {
      "version": "6.5.1",
      "resolved": "https://registry.npmjs.org/css-loader/-/css-loader-6.5.1.tgz",
      "integrity": "sha512-gEy2w9AnJNnD9Kuo4XAP9VflW/ujKoS9c/syO+uWMlm5igc7LysKzPXaDoR2vroROkSwsTS2tGr1yGGEbZOYZQ==",
      "dev": true,
      "dependencies": {
        "icss-utils": "^5.1.0",
        "postcss": "^8.2.15",
        "postcss-modules-extract-imports": "^3.0.0",
        "postcss-modules-local-by-default": "^4.0.0",
        "postcss-modules-scope": "^3.0.0",
        "postcss-modules-values": "^4.0.0",
        "postcss-value-parser": "^4.1.0",
        "semver": "^7.3.5"
      },
      "engines": {
        "node": ">= 12.13.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/webpack"
      },
      "peerDependencies": {
        "webpack": "^5.0.0"
      }
    },
    "node_modules/css-prefers-color-scheme": {
      "version": "6.0.2",
      "resolved": "https://registry.npmjs.org/css-prefers-color-scheme/-/css-prefers-color-scheme-6.0.2.tgz",
      "integrity": "sha512-gv0KQBEM+q/XdoKyznovq3KW7ocO7k+FhPP+hQR1MenJdu0uPGS6IZa9PzlbqBeS6XcZJNAoqoFxlAUW461CrA==",
      "dev": true,
      "bin": {
        "css-prefers-color-scheme": "dist/cli.cjs"
      },
      "engines": {
        "node": "^12 || ^14 || >=16"
      },
      "peerDependencies": {
        "postcss": "^8.3"
      }
    },
    "node_modules/css-select": {
      "version": "4.2.1",
      "resolved": "https://registry.npmjs.org/css-select/-/css-select-4.2.1.tgz",
      "integrity": "sha512-/aUslKhzkTNCQUB2qTX84lVmfia9NyjP3WpDGtj/WxhwBzWBYUV3DgUpurHTme8UTPcPlAD1DJ+b0nN/t50zDQ==",
      "dev": true,
      "dependencies": {
        "boolbase": "^1.0.0",
        "css-what": "^5.1.0",
        "domhandler": "^4.3.0",
        "domutils": "^2.8.0",
        "nth-check": "^2.0.1"
      },
      "funding": {
        "url": "https://github.com/sponsors/fb55"
      }
    },
    "node_modules/css-what": {
      "version": "5.1.0",
      "resolved": "https://registry.npmjs.org/css-what/-/css-what-5.1.0.tgz",
      "integrity": "sha512-arSMRWIIFY0hV8pIxZMEfmMI47Wj3R/aWpZDDxWYCPEiOMv6tfOrnpDtgxBYPEQD4V0Y/958+1TdC3iWTFcUPw==",
      "dev": true,
      "engines": {
        "node": ">= 6"
      },
      "funding": {
        "url": "https://github.com/sponsors/fb55"
      }
    },
    "node_modules/css/node_modules/source-map": {
      "version": "0.6.1",
      "resolved": "https://registry.npmjs.org/source-map/-/source-map-0.6.1.tgz",
      "integrity": "sha512-UjgapumWlbMhkBgzT7Ykc5YXUT46F0iKu8SGXq0bcwP5dz/h0Plj6enJqjz1Zbq2l5WaqYnrVbwWOWMyF3F47g==",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/cssdb": {
      "version": "5.1.0",
      "resolved": "https://registry.npmjs.org/cssdb/-/cssdb-5.1.0.tgz",
      "integrity": "sha512-/vqjXhv1x9eGkE/zO6o8ZOI7dgdZbLVLUGyVRbPgk6YipXbW87YzUCcO+Jrmi5bwJlAH6oD+MNeZyRgXea1GZw==",
      "dev": true
    },
    "node_modules/cssesc": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/cssesc/-/cssesc-3.0.0.tgz",
      "integrity": "sha512-/Tb/JcjK111nNScGob5MNtsntNM1aCNUDipB/TkwZFhyDrrE47SOx/18wF2bbjgc3ZzCSKW1T5nt5EbFoAz/Vg==",
      "dev": true,
      "bin": {
        "cssesc": "bin/cssesc"
      },
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/custom-event": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/custom-event/-/custom-event-1.0.1.tgz",
      "integrity": "sha1-XQKkaFCt8bSjF5RqOSj8y1v9BCU=",
      "dev": true
    },
    "node_modules/date-format": {
      "version": "4.0.3",
      "resolved": "https://registry.npmjs.org/date-format/-/date-format-4.0.3.tgz",
      "integrity": "sha512-7P3FyqDcfeznLZp2b+OMitV9Sz2lUnsT87WaTat9nVwqsBkTzPG3lPLNwW3en6F4pHUiWzr6vb8CLhjdK9bcxQ==",
      "dev": true,
      "engines": {
        "node": ">=4.0"
      }
    },
    "node_modules/debug": {
      "version": "4.3.3",
      "resolved": "https://registry.npmjs.org/debug/-/debug-4.3.3.tgz",
      "integrity": "sha512-/zxw5+vh1Tfv+4Qn7a5nsbcJKPaSvCDhojn6FEl9vupwK2VCSDtEiEtqr8DFtzYFOdz63LBkxec7DYuc2jon6Q==",
      "dependencies": {
        "ms": "2.1.2"
      },
      "engines": {
        "node": ">=6.0"
      },
      "peerDependenciesMeta": {
        "supports-color": {
          "optional": true
        }
      }
    },
    "node_modules/decode-uri-component": {
      "version": "0.2.0",
      "resolved": "https://registry.npmjs.org/decode-uri-component/-/decode-uri-component-0.2.0.tgz",
      "integrity": "sha1-6zkTMzRYd1y4TNGh+uBiEGu4dUU=",
      "dev": true,
      "engines": {
        "node": ">=0.10"
      }
    },
    "node_modules/decompress-response": {
      "version": "3.3.0",
      "resolved": "https://registry.npmjs.org/decompress-response/-/decompress-response-3.3.0.tgz",
      "integrity": "sha1-gKTdMjdIOEv6JICDYirt7Jgq3/M=",
      "dependencies": {
        "mimic-response": "^1.0.0"
      },
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/deep-equal": {
      "version": "1.1.1",
      "resolved": "https://registry.npmjs.org/deep-equal/-/deep-equal-1.1.1.tgz",
      "integrity": "sha512-yd9c5AdiqVcR+JjcwUQb9DkhJc8ngNr0MahEBGvDiJw8puWab2yZlh+nkasOnZP+EGTAP6rRp2JzJhJZzvNF8g==",
      "dev": true,
      "dependencies": {
        "is-arguments": "^1.0.4",
        "is-date-object": "^1.0.1",
        "is-regex": "^1.0.4",
        "object-is": "^1.0.1",
        "object-keys": "^1.1.1",
        "regexp.prototype.flags": "^1.2.0"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/deep-extend": {
      "version": "0.6.0",
      "resolved": "https://registry.npmjs.org/deep-extend/-/deep-extend-0.6.0.tgz",
      "integrity": "sha512-LOHxIOaPYdHlJRtCQfDIVZtfw/ufM8+rVj649RIHzcm/vGwQRXFt6OPqIFWsm2XEMrNIEtWR64sY1LEKD2vAOA==",
      "engines": {
        "node": ">=4.0.0"
      }
    },
    "node_modules/default-gateway": {
      "version": "6.0.3",
      "resolved": "https://registry.npmjs.org/default-gateway/-/default-gateway-6.0.3.tgz",
      "integrity": "sha512-fwSOJsbbNzZ/CUFpqFBqYfYNLj1NbMPm8MMCIzHjC83iSJRBEGmDUxU+WP661BaBQImeC2yHwXtz+P/O9o+XEg==",
      "dev": true,
      "dependencies": {
        "execa": "^5.0.0"
      },
      "engines": {
        "node": ">= 10"
      }
    },
    "node_modules/defaults": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/defaults/-/defaults-1.0.3.tgz",
      "integrity": "sha1-xlYFHpgX2f8I7YgUd/P+QBnz730=",
      "dev": true,
      "dependencies": {
        "clone": "^1.0.2"
      }
    },
    "node_modules/defer-to-connect": {
      "version": "1.1.3",
      "resolved": "https://registry.npmjs.org/defer-to-connect/-/defer-to-connect-1.1.3.tgz",
      "integrity": "sha512-0ISdNousHvZT2EiFlZeZAHBUvSxmKswVCEf8hW7KWgG4a8MVEu/3Vb6uWYozkjylyCxe0JBIiRB1jV45S70WVQ=="
    },
    "node_modules/define-lazy-prop": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/define-lazy-prop/-/define-lazy-prop-2.0.0.tgz",
      "integrity": "sha512-Ds09qNh8yw3khSjiJjiUInaGX9xlqZDY7JVryGxdxV7NPeuqQfplOpQ66yJFZut3jLa5zOwkXw1g9EI2uKh4Og==",
      "dev": true,
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/define-properties": {
      "version": "1.1.3",
      "resolved": "https://registry.npmjs.org/define-properties/-/define-properties-1.1.3.tgz",
      "integrity": "sha512-3MqfYKj2lLzdMSf8ZIZE/V+Zuy+BgD6f164e8K2w7dgnpKArBDerGYpM46IYYcjnkdPNMjPk9A6VFB8+3SKlXQ==",
      "dev": true,
      "dependencies": {
        "object-keys": "^1.0.12"
      },
      "engines": {
        "node": ">= 0.4"
      }
    },
    "node_modules/del": {
      "version": "6.0.0",
      "resolved": "https://registry.npmjs.org/del/-/del-6.0.0.tgz",
      "integrity": "sha512-1shh9DQ23L16oXSZKB2JxpL7iMy2E0S9d517ptA1P8iw0alkPtQcrKH7ru31rYtKwF499HkTu+DRzq3TCKDFRQ==",
      "dev": true,
      "dependencies": {
        "globby": "^11.0.1",
        "graceful-fs": "^4.2.4",
        "is-glob": "^4.0.1",
        "is-path-cwd": "^2.2.0",
        "is-path-inside": "^3.0.2",
        "p-map": "^4.0.0",
        "rimraf": "^3.0.2",
        "slash": "^3.0.0"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/del/node_modules/array-union": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/array-union/-/array-union-2.1.0.tgz",
      "integrity": "sha512-HGyxoOTYUyCM6stUe6EJgnd4EoewAI7zMdfqO+kGjnlZmBDz/cR5pf8r/cR4Wq60sL/p0IkcjUEEPwS3GFrIyw==",
      "dev": true,
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/del/node_modules/globby": {
      "version": "11.1.0",
      "resolved": "https://registry.npmjs.org/globby/-/globby-11.1.0.tgz",
      "integrity": "sha512-jhIXaOzy1sb8IyocaruWSn1TjmnBVs8Ayhcy83rmxNJ8q2uWKCAj3CnJY+KpGSXCueAPc0i05kVvVKtP1t9S3g==",
      "dev": true,
      "dependencies": {
        "array-union": "^2.1.0",
        "dir-glob": "^3.0.1",
        "fast-glob": "^3.2.9",
        "ignore": "^5.2.0",
        "merge2": "^1.4.1",
        "slash": "^3.0.0"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/del/node_modules/slash": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/slash/-/slash-3.0.0.tgz",
      "integrity": "sha512-g9Q1haeby36OSStwb4ntCGGGaKsaVSjQ68fBxoQcutl5fS1vuY18H3wSt3jFyFtrkx+Kz0V1G85A4MyAdDMi2Q==",
      "dev": true,
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/delegates": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/delegates/-/delegates-1.0.0.tgz",
      "integrity": "sha1-hMbhWbgZBP3KWaDvRM2HDTElD5o=",
      "dev": true
    },
    "node_modules/depd": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/depd/-/depd-1.1.2.tgz",
      "integrity": "sha1-m81S4UwJd2PnSbJ0xDRu0uVgtak=",
      "engines": {
        "node": ">= 0.6"
      }
    },
    "node_modules/dependency-graph": {
      "version": "0.11.0",
      "resolved": "https://registry.npmjs.org/dependency-graph/-/dependency-graph-0.11.0.tgz",
      "integrity": "sha512-JeMq7fEshyepOWDfcfHK06N3MhyPhz++vtqWhMT5O9A3K42rdsEDpfdVqjaqaAhsw6a+ZqeDvQVtD0hFHQWrzg==",
      "dev": true,
      "engines": {
        "node": ">= 0.6.0"
      }
    },
    "node_modules/destroy": {
      "version": "1.0.4",
      "resolved": "https://registry.npmjs.org/destroy/-/destroy-1.0.4.tgz",
      "integrity": "sha1-l4hXRCxEdJ5CBmE+N5RiBYJqvYA="
    },
    "node_modules/detect-node": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/detect-node/-/detect-node-2.1.0.tgz",
      "integrity": "sha512-T0NIuQpnTvFDATNuHN5roPwSBG83rFsuO+MXXH9/3N1eFbn4wcPjttvjMLEPWJ0RGUYgQE7cGgS3tNxbqCGM7g==",
      "dev": true
    },
    "node_modules/di": {
      "version": "0.0.1",
      "resolved": "https://registry.npmjs.org/di/-/di-0.0.1.tgz",
      "integrity": "sha1-gGZJMmzqp8qjMG112YXqJ0i6kTw=",
      "dev": true
    },
    "node_modules/dir-glob": {
      "version": "3.0.1",
      "resolved": "https://registry.npmjs.org/dir-glob/-/dir-glob-3.0.1.tgz",
      "integrity": "sha512-WkrWp9GR4KXfKGYzOLmTuGVi1UWFfws377n9cc55/tb6DuqyF6pcQ5AbiHEshaDpY9v6oaSr2XCDidGmMwdzIA==",
      "dev": true,
      "dependencies": {
        "path-type": "^4.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/dns-equal": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/dns-equal/-/dns-equal-1.0.0.tgz",
      "integrity": "sha1-s55/HabrCnW6nBcySzR1PEfgZU0=",
      "dev": true
    },
    "node_modules/dns-packet": {
      "version": "1.3.4",
      "resolved": "https://registry.npmjs.org/dns-packet/-/dns-packet-1.3.4.tgz",
      "integrity": "sha512-BQ6F4vycLXBvdrJZ6S3gZewt6rcrks9KBgM9vrhW+knGRqc8uEdT7fuCwloc7nny5xNoMJ17HGH0R/6fpo8ECA==",
      "dev": true,
      "dependencies": {
        "ip": "^1.1.0",
        "safe-buffer": "^5.0.1"
      }
    },
    "node_modules/dns-txt": {
      "version": "2.0.2",
      "resolved": "https://registry.npmjs.org/dns-txt/-/dns-txt-2.0.2.tgz",
      "integrity": "sha1-uR2Ab10nGI5Ks+fRB9iBocxGQrY=",
      "dev": true,
      "dependencies": {
        "buffer-indexof": "^1.0.0"
      }
    },
    "node_modules/dom-serialize": {
      "version": "2.2.1",
      "resolved": "https://registry.npmjs.org/dom-serialize/-/dom-serialize-2.2.1.tgz",
      "integrity": "sha1-ViromZ9Evl6jB29UGdzVnrQ6yVs=",
      "dev": true,
      "dependencies": {
        "custom-event": "~1.0.0",
        "ent": "~2.2.0",
        "extend": "^3.0.0",
        "void-elements": "^2.0.0"
      }
    },
    "node_modules/dom-serializer": {
      "version": "1.3.2",
      "resolved": "https://registry.npmjs.org/dom-serializer/-/dom-serializer-1.3.2.tgz",
      "integrity": "sha512-5c54Bk5Dw4qAxNOI1pFEizPSjVsx5+bpJKmL2kPn8JhBUq2q09tTCa3mjijun2NfK78NMouDYNMBkOrPZiS+ig==",
      "dev": true,
      "dependencies": {
        "domelementtype": "^2.0.1",
        "domhandler": "^4.2.0",
        "entities": "^2.0.0"
      },
      "funding": {
        "url": "https://github.com/cheeriojs/dom-serializer?sponsor=1"
      }
    },
    "node_modules/domelementtype": {
      "version": "2.2.0",
      "resolved": "https://registry.npmjs.org/domelementtype/-/domelementtype-2.2.0.tgz",
      "integrity": "sha512-DtBMo82pv1dFtUmHyr48beiuq792Sxohr+8Hm9zoxklYPfa6n0Z3Byjj2IV7bmr2IyqClnqEQhfgHJJ5QF0R5A==",
      "dev": true,
      "funding": [
        {
          "type": "github",
          "url": "https://github.com/sponsors/fb55"
        }
      ]
    },
    "node_modules/domhandler": {
      "version": "4.3.0",
      "resolved": "https://registry.npmjs.org/domhandler/-/domhandler-4.3.0.tgz",
      "integrity": "sha512-fC0aXNQXqKSFTr2wDNZDhsEYjCiYsDWl3D01kwt25hm1YIPyDGHvvi3rw+PLqHAl/m71MaiF7d5zvBr0p5UB2g==",
      "dev": true,
      "dependencies": {
        "domelementtype": "^2.2.0"
      },
      "engines": {
        "node": ">= 4"
      },
      "funding": {
        "url": "https://github.com/fb55/domhandler?sponsor=1"
      }
    },
    "node_modules/domutils": {
      "version": "2.8.0",
      "resolved": "https://registry.npmjs.org/domutils/-/domutils-2.8.0.tgz",
      "integrity": "sha512-w96Cjofp72M5IIhpjgobBimYEfoPjx1Vx0BSX9P30WBdZW2WIKU0T1Bd0kz2eNZ9ikjKgHbEyKx8BB6H1L3h3A==",
      "dev": true,
      "dependencies": {
        "dom-serializer": "^1.0.1",
        "domelementtype": "^2.2.0",
        "domhandler": "^4.2.0"
      },
      "funding": {
        "url": "https://github.com/fb55/domutils?sponsor=1"
      }
    },
    "node_modules/dot-prop": {
      "version": "5.3.0",
      "resolved": "https://registry.npmjs.org/dot-prop/-/dot-prop-5.3.0.tgz",
      "integrity": "sha512-QM8q3zDe58hqUqjraQOmzZ1LIH9SWQJTlEKCH4kJ2oQvLZk7RbQXvtDM2XEq3fwkV9CCvvH4LA0AV+ogFsBM2Q==",
      "dependencies": {
        "is-obj": "^2.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/duplexer3": {
      "version": "0.1.4",
      "resolved": "https://registry.npmjs.org/duplexer3/-/duplexer3-0.1.4.tgz",
      "integrity": "sha1-7gHdHKwO08vH/b6jfcCo8c4ALOI="
    },
    "node_modules/ee-first": {
      "version": "1.1.1",
      "resolved": "https://registry.npmjs.org/ee-first/-/ee-first-1.1.1.tgz",
      "integrity": "sha1-WQxhFWsK4vTwJVcyoViyZrxWsh0="
    },
    "node_modules/electron-to-chromium": {
      "version": "1.4.56",
      "resolved": "https://registry.npmjs.org/electron-to-chromium/-/electron-to-chromium-1.4.56.tgz",
      "integrity": "sha512-0k/S0FQqRRpJbX7YUjwCcLZ8D42RqGKtaiq90adXBOYgTIWwLA/g3toO8k9yEpqU8iC4QyaWYYWSTBIna8WV4g==",
      "dev": true
    },
    "node_modules/emoji-regex": {
      "version": "8.0.0",
      "resolved": "https://registry.npmjs.org/emoji-regex/-/emoji-regex-8.0.0.tgz",
      "integrity": "sha512-MSjYzcWNOA0ewAHpz0MxpYFvwg6yjy1NG3xteoqz644VCo/RPgnr1/GGt+ic3iJTzQ8Eu3TdM14SawnVUmGE6A=="
    },
    "node_modules/emojis-list": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/emojis-list/-/emojis-list-3.0.0.tgz",
      "integrity": "sha512-/kyM18EfinwXZbno9FyUGeFh87KC8HRQBQGildHZbEuRyWFOmv1U10o9BBp8XVZDVNNuQKyIGIu5ZYAAXJ0V2Q==",
      "dev": true,
      "engines": {
        "node": ">= 4"
      }
    },
    "node_modules/encodeurl": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/encodeurl/-/encodeurl-1.0.2.tgz",
      "integrity": "sha1-rT/0yG7C0CkyL1oCw6mmBslbP1k=",
      "engines": {
        "node": ">= 0.8"
      }
    },
    "node_modules/encoding": {
      "version": "0.1.13",
      "resolved": "https://registry.npmjs.org/encoding/-/encoding-0.1.13.tgz",
      "integrity": "sha512-ETBauow1T35Y/WZMkio9jiM0Z5xjHHmJ4XmjZOq1l/dXz3lr2sRn87nJy20RupqSh1F2m3HHPSp8ShIPQJrJ3A==",
      "dev": true,
      "optional": true,
      "dependencies": {
        "iconv-lite": "^0.6.2"
      }
    },
    "node_modules/encoding/node_modules/iconv-lite": {
      "version": "0.6.3",
      "resolved": "https://registry.npmjs.org/iconv-lite/-/iconv-lite-0.6.3.tgz",
      "integrity": "sha512-4fCk79wshMdzMp2rH06qWrJE4iolqLhCUH+OiuIgU++RB0+94NlDL81atO7GX55uUKueo0txHNtvEyI6D7WdMw==",
      "dev": true,
      "optional": true,
      "dependencies": {
        "safer-buffer": ">= 2.1.2 < 3.0.0"
      },
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/end-of-stream": {
      "version": "1.4.4",
      "resolved": "https://registry.npmjs.org/end-of-stream/-/end-of-stream-1.4.4.tgz",
      "integrity": "sha512-+uw1inIHVPQoaVuHzRyXd21icM+cnt4CzD5rW+NC1wjOUSTOs+Te7FOv7AhN7vS9x/oIyhLP5PR1H+phQAHu5Q==",
      "dependencies": {
        "once": "^1.4.0"
      }
    },
    "node_modules/engine.io": {
      "version": "6.1.2",
      "resolved": "https://registry.npmjs.org/engine.io/-/engine.io-6.1.2.tgz",
      "integrity": "sha512-v/7eGHxPvO2AWsksyx2PUsQvBafuvqs0jJJQ0FdmJG1b9qIvgSbqDRGwNhfk2XHaTTbTXiC4quRE8Q9nRjsrQQ==",
      "dev": true,
      "dependencies": {
        "@types/cookie": "^0.4.1",
        "@types/cors": "^2.8.12",
        "@types/node": ">=10.0.0",
        "accepts": "~1.3.4",
        "base64id": "2.0.0",
        "cookie": "~0.4.1",
        "cors": "~2.8.5",
        "debug": "~4.3.1",
        "engine.io-parser": "~5.0.0",
        "ws": "~8.2.3"
      },
      "engines": {
        "node": ">=10.0.0"
      }
    },
    "node_modules/engine.io-parser": {
      "version": "5.0.3",
      "resolved": "https://registry.npmjs.org/engine.io-parser/-/engine.io-parser-5.0.3.tgz",
      "integrity": "sha512-BtQxwF27XUNnSafQLvDi0dQ8s3i6VgzSoQMJacpIcGNrlUdfHSKbgm3jmjCVvQluGzqwujQMPAoMai3oYSTurg==",
      "dev": true,
      "dependencies": {
        "@socket.io/base64-arraybuffer": "~1.0.2"
      },
      "engines": {
        "node": ">=10.0.0"
      }
    },
    "node_modules/enhanced-resolve": {
      "version": "5.8.3",
      "resolved": "https://registry.npmjs.org/enhanced-resolve/-/enhanced-resolve-5.8.3.tgz",
      "integrity": "sha512-EGAbGvH7j7Xt2nc0E7D99La1OiEs8LnyimkRgwExpUMScN6O+3x9tIWs7PLQZVNx4YD+00skHXPXi1yQHpAmZA==",
      "dev": true,
      "dependencies": {
        "graceful-fs": "^4.2.4",
        "tapable": "^2.2.0"
      },
      "engines": {
        "node": ">=10.13.0"
      }
    },
    "node_modules/ent": {
      "version": "2.2.0",
      "resolved": "https://registry.npmjs.org/ent/-/ent-2.2.0.tgz",
      "integrity": "sha1-6WQhkyWiHQX0RGai9obtbOX13R0=",
      "dev": true
    },
    "node_modules/entities": {
      "version": "2.2.0",
      "resolved": "https://registry.npmjs.org/entities/-/entities-2.2.0.tgz",
      "integrity": "sha512-p92if5Nz619I0w+akJrLZH0MX0Pb5DX39XOwQTtXSdQQOaYH03S1uIQp4mhOZtAXrxq4ViO67YTiLBo2638o9A==",
      "dev": true,
      "funding": {
        "url": "https://github.com/fb55/entities?sponsor=1"
      }
    },
    "node_modules/env-paths": {
      "version": "2.2.1",
      "resolved": "https://registry.npmjs.org/env-paths/-/env-paths-2.2.1.tgz",
      "integrity": "sha512-+h1lkLKhZMTYjog1VEpJNG7NZJWcuc2DDk/qsqSTRRCOXiLjeQ1d1/udrUGhqMxUgAlwKNZ0cf2uqan5GLuS2A==",
      "dev": true,
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/err-code": {
      "version": "2.0.3",
      "resolved": "https://registry.npmjs.org/err-code/-/err-code-2.0.3.tgz",
      "integrity": "sha512-2bmlRpNKBxT/CRmPOlyISQpNj+qSeYvcym/uT0Jx2bMOlKLtSy1ZmLuVxSEKKyor/N5yhvp/ZiG1oE3DEYMSFA==",
      "dev": true
    },
    "node_modules/errno": {
      "version": "0.1.8",
      "resolved": "https://registry.npmjs.org/errno/-/errno-0.1.8.tgz",
      "integrity": "sha512-dJ6oBr5SQ1VSd9qkk7ByRgb/1SH4JZjCHSW/mr63/QcXO9zLVxvJ6Oy13nio03rxpSnVDDjFor75SjVeZWPW/A==",
      "dev": true,
      "optional": true,
      "dependencies": {
        "prr": "~1.0.1"
      },
      "bin": {
        "errno": "cli.js"
      }
    },
    "node_modules/error-ex": {
      "version": "1.3.2",
      "resolved": "https://registry.npmjs.org/error-ex/-/error-ex-1.3.2.tgz",
      "integrity": "sha512-7dFHNmqeFSEt2ZBsCriorKnn3Z2pj+fd9kmI6QoWw4//DL+icEBfc0U7qJCisqrTsKTjw4fNFy2pW9OqStD84g==",
      "dev": true,
      "dependencies": {
        "is-arrayish": "^0.2.1"
      }
    },
    "node_modules/errorhandler": {
      "version": "1.5.1",
      "resolved": "https://registry.npmjs.org/errorhandler/-/errorhandler-1.5.1.tgz",
      "integrity": "sha512-rcOwbfvP1WTViVoUjcfZicVzjhjTuhSMntHh6mW3IrEiyE6mJyXvsToJUJGlGlw/2xU9P5whlWNGlIDVeCiT4A==",
      "dependencies": {
        "accepts": "~1.3.7",
        "escape-html": "~1.0.3"
      },
      "engines": {
        "node": ">= 0.8"
      }
    },
    "node_modules/es-module-lexer": {
      "version": "0.9.3",
      "resolved": "https://registry.npmjs.org/es-module-lexer/-/es-module-lexer-0.9.3.tgz",
      "integrity": "sha512-1HQ2M2sPtxwnvOvT1ZClHyQDiggdNjURWpY2we6aMKCQiUVxTmVs2UYPLIrD84sS+kMdUwfBSylbJPwNnBrnHQ==",
      "dev": true
    },
    "node_modules/esbuild": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild/-/esbuild-0.14.11.tgz",
      "integrity": "sha512-xZvPtVj6yecnDeFb3KjjCM6i7B5TCAQZT77kkW/CpXTMnd6VLnRPKrUB1XHI1pSq6a4Zcy3BGueQ8VljqjDGCg==",
      "dev": true,
      "hasInstallScript": true,
      "optional": true,
      "bin": {
        "esbuild": "bin/esbuild"
      },
      "optionalDependencies": {
        "esbuild-android-arm64": "0.14.11",
        "esbuild-darwin-64": "0.14.11",
        "esbuild-darwin-arm64": "0.14.11",
        "esbuild-freebsd-64": "0.14.11",
        "esbuild-freebsd-arm64": "0.14.11",
        "esbuild-linux-32": "0.14.11",
        "esbuild-linux-64": "0.14.11",
        "esbuild-linux-arm": "0.14.11",
        "esbuild-linux-arm64": "0.14.11",
        "esbuild-linux-mips64le": "0.14.11",
        "esbuild-linux-ppc64le": "0.14.11",
        "esbuild-linux-s390x": "0.14.11",
        "esbuild-netbsd-64": "0.14.11",
        "esbuild-openbsd-64": "0.14.11",
        "esbuild-sunos-64": "0.14.11",
        "esbuild-windows-32": "0.14.11",
        "esbuild-windows-64": "0.14.11",
        "esbuild-windows-arm64": "0.14.11"
      }
    },
    "node_modules/esbuild-android-arm64": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-android-arm64/-/esbuild-android-arm64-0.14.11.tgz",
      "integrity": "sha512-6iHjgvMnC/SzDH8TefL+/3lgCjYWwAd1LixYfmz/TBPbDQlxcuSkX0yiQgcJB9k+ibZ54yjVXziIwGdlc+6WNw==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "android"
      ]
    },
    "node_modules/esbuild-darwin-64": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-darwin-64/-/esbuild-darwin-64-0.14.11.tgz",
      "integrity": "sha512-olq84ikh6TiBcrs3FnM4eR5VPPlcJcdW8BnUz/lNoEWYifYQ+Po5DuYV1oz1CTFMw4k6bQIZl8T3yxL+ZT2uvQ==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "darwin"
      ]
    },
    "node_modules/esbuild-darwin-arm64": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-darwin-arm64/-/esbuild-darwin-arm64-0.14.11.tgz",
      "integrity": "sha512-Jj0ieWLREPBYr/TZJrb2GFH8PVzDqiQWavo1pOFFShrcmHWDBDrlDxPzEZ67NF/Un3t6sNNmeI1TUS/fe1xARg==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "darwin"
      ]
    },
    "node_modules/esbuild-freebsd-64": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-freebsd-64/-/esbuild-freebsd-64-0.14.11.tgz",
      "integrity": "sha512-C5sT3/XIztxxz/zwDjPRHyzj/NJFOnakAanXuyfLDwhwupKPd76/PPHHyJx6Po6NI6PomgVp/zi6GRB8PfrOTA==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "freebsd"
      ]
    },
    "node_modules/esbuild-freebsd-arm64": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-freebsd-arm64/-/esbuild-freebsd-arm64-0.14.11.tgz",
      "integrity": "sha512-y3Llu4wbs0bk4cwjsdAtVOesXb6JkdfZDLKMt+v1U3tOEPBdSu6w8796VTksJgPfqvpX22JmPLClls0h5p+L9w==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "freebsd"
      ]
    },
    "node_modules/esbuild-linux-32": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-linux-32/-/esbuild-linux-32-0.14.11.tgz",
      "integrity": "sha512-Cg3nVsxArjyLke9EuwictFF3Sva+UlDTwHIuIyx8qpxRYAOUTmxr2LzYrhHyTcGOleLGXUXYsnUVwKqnKAgkcg==",
      "cpu": [
        "ia32"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/esbuild-linux-64": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-linux-64/-/esbuild-linux-64-0.14.11.tgz",
      "integrity": "sha512-oeR6dIrrojr8DKVrxtH3xl4eencmjsgI6kPkDCRIIFwv4p+K7ySviM85K66BN01oLjzthpUMvBVfWSJkBLeRbg==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/esbuild-linux-arm": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-linux-arm/-/esbuild-linux-arm-0.14.11.tgz",
      "integrity": "sha512-vcwskfD9g0tojux/ZaTJptJQU3a7YgTYsptK1y6LQ/rJmw7U5QJvboNawqM98Ca3ToYEucfCRGbl66OTNtp6KQ==",
      "cpu": [
        "arm"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/esbuild-linux-arm64": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-linux-arm64/-/esbuild-linux-arm64-0.14.11.tgz",
      "integrity": "sha512-+e6ZCgTFQYZlmg2OqLkg1jHLYtkNDksxWDBWNtI4XG4WxuOCUErLqfEt9qWjvzK3XBcCzHImrajkUjO+rRkbMg==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/esbuild-linux-mips64le": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-linux-mips64le/-/esbuild-linux-mips64le-0.14.11.tgz",
      "integrity": "sha512-Rrs99L+p54vepmXIb87xTG6ukrQv+CzrM8eoeR+r/OFL2Rg8RlyEtCeshXJ2+Q66MXZOgPJaokXJZb9snq28bw==",
      "cpu": [
        "mips64el"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/esbuild-linux-ppc64le": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-linux-ppc64le/-/esbuild-linux-ppc64le-0.14.11.tgz",
      "integrity": "sha512-JyzziGAI0D30Vyzt0HDihp4s1IUtJ3ssV2zx9O/c+U/dhUHVP2TmlYjzCfCr2Q6mwXTeloDcLS4qkyvJtYptdQ==",
      "cpu": [
        "ppc64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/esbuild-linux-s390x": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-linux-s390x/-/esbuild-linux-s390x-0.14.11.tgz",
      "integrity": "sha512-DoThrkzunZ1nfRGoDN6REwmo8ZZWHd2ztniPVIR5RMw/Il9wiWEYBahb8jnMzQaSOxBsGp0PbyJeVLTUatnlcw==",
      "cpu": [
        "s390x"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/esbuild-netbsd-64": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-netbsd-64/-/esbuild-netbsd-64-0.14.11.tgz",
      "integrity": "sha512-12luoRQz+6eihKYh1zjrw0CBa2aw3twIiHV/FAfjh2NEBDgJQOY4WCEUEN+Rgon7xmLh4XUxCQjnwrvf8zhACw==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "netbsd"
      ]
    },
    "node_modules/esbuild-openbsd-64": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-openbsd-64/-/esbuild-openbsd-64-0.14.11.tgz",
      "integrity": "sha512-l18TZDjmvwW6cDeR4fmizNoxndyDHamGOOAenwI4SOJbzlJmwfr0jUgjbaXCUuYVOA964siw+Ix+A+bhALWg8Q==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "openbsd"
      ]
    },
    "node_modules/esbuild-sunos-64": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-sunos-64/-/esbuild-sunos-64-0.14.11.tgz",
      "integrity": "sha512-bmYzDtwASBB8c+0/HVOAiE9diR7+8zLm/i3kEojUH2z0aIs6x/S4KiTuT5/0VKJ4zk69kXel1cNWlHBMkmavQg==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "sunos"
      ]
    },
    "node_modules/esbuild-wasm": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-wasm/-/esbuild-wasm-0.14.11.tgz",
      "integrity": "sha512-9e1R6hv0hiU+BkJI2edqUuWfXUbOP2Mox+Ijl/uY1vLLlSsunkrcADqD/4Rz+VCEDzw6ecscJM+uJqR2fRmEUg==",
      "dev": true,
      "bin": {
        "esbuild": "bin/esbuild"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/esbuild-windows-32": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-windows-32/-/esbuild-windows-32-0.14.11.tgz",
      "integrity": "sha512-J1Ys5hMid8QgdY00OBvIolXgCQn1ARhYtxPnG6ESWNTty3ashtc4+As5nTrsErnv8ZGUcWZe4WzTP/DmEVX1UQ==",
      "cpu": [
        "ia32"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "win32"
      ]
    },
    "node_modules/esbuild-windows-64": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-windows-64/-/esbuild-windows-64-0.14.11.tgz",
      "integrity": "sha512-h9FmMskMuGeN/9G9+LlHPAoiQk9jlKDUn9yA0MpiGzwLa82E7r1b1u+h2a+InprbSnSLxDq/7p5YGtYVO85Mlg==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "win32"
      ]
    },
    "node_modules/esbuild-windows-arm64": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-windows-arm64/-/esbuild-windows-arm64-0.14.11.tgz",
      "integrity": "sha512-dZp7Krv13KpwKklt9/1vBFBMqxEQIO6ri7Azf8C+ob4zOegpJmha2XY9VVWP/OyQ0OWk6cEeIzMJwInRZrzBUQ==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "win32"
      ]
    },
    "node_modules/escalade": {
      "version": "3.1.1",
      "resolved": "https://registry.npmjs.org/escalade/-/escalade-3.1.1.tgz",
      "integrity": "sha512-k0er2gUkLf8O0zKJiAhmkTnJlTvINGv7ygDNPbeIsX/TJjGJZHuh9B2UxbsaEkmlEo9MfhrSzmhIlhRlI2GXnw==",
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/escape-goat": {
      "version": "2.1.1",
      "resolved": "https://registry.npmjs.org/escape-goat/-/escape-goat-2.1.1.tgz",
      "integrity": "sha512-8/uIhbG12Csjy2JEW7D9pHbreaVaS/OpN3ycnyvElTdwM5n6GY6W6e2IPemfvGZeUMqZ9A/3GqIZMgKnBhAw/Q==",
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/escape-html": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/escape-html/-/escape-html-1.0.3.tgz",
      "integrity": "sha1-Aljq5NPQwJdN4cFpGI7wBR0dGYg="
    },
    "node_modules/escape-string-regexp": {
      "version": "1.0.5",
      "resolved": "https://registry.npmjs.org/escape-string-regexp/-/escape-string-regexp-1.0.5.tgz",
      "integrity": "sha1-G2HAViGQqN/2rjuyzwIAyhMLhtQ=",
      "dev": true,
      "engines": {
        "node": ">=0.8.0"
      }
    },
    "node_modules/eslint-scope": {
      "version": "5.1.1",
      "resolved": "https://registry.npmjs.org/eslint-scope/-/eslint-scope-5.1.1.tgz",
      "integrity": "sha512-2NxwbF/hZ0KpepYN0cNbo+FN6XoK7GaHlQhgx/hIZl6Va0bF45RQOOwhLIy8lQDbuCiadSLCBnH2CFYquit5bw==",
      "dev": true,
      "dependencies": {
        "esrecurse": "^4.3.0",
        "estraverse": "^4.1.1"
      },
      "engines": {
        "node": ">=8.0.0"
      }
    },
    "node_modules/esprima": {
      "version": "4.0.1",
      "resolved": "https://registry.npmjs.org/esprima/-/esprima-4.0.1.tgz",
      "integrity": "sha512-eGuFFw7Upda+g4p+QHvnW0RyTX/SVeJBDM/gCtMARO0cLuT2HcEKnTPvhjV6aGeqrCB/sbNop0Kszm0jsaWU4A==",
      "dev": true,
      "bin": {
        "esparse": "bin/esparse.js",
        "esvalidate": "bin/esvalidate.js"
      },
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/esrecurse": {
      "version": "4.3.0",
      "resolved": "https://registry.npmjs.org/esrecurse/-/esrecurse-4.3.0.tgz",
      "integrity": "sha512-KmfKL3b6G+RXvP8N1vr3Tq1kL/oCFgn2NYXEtqP8/L3pKapUA4G8cFVaoF3SU323CD4XypR/ffioHmkti6/Tag==",
      "dev": true,
      "dependencies": {
        "estraverse": "^5.2.0"
      },
      "engines": {
        "node": ">=4.0"
      }
    },
    "node_modules/esrecurse/node_modules/estraverse": {
      "version": "5.3.0",
      "resolved": "https://registry.npmjs.org/estraverse/-/estraverse-5.3.0.tgz",
      "integrity": "sha512-MMdARuVEQziNTeJD8DgMqmhwR11BRQ/cBP+pLtYdSTnf3MIO8fFeiINEbX36ZdNlfU/7A9f3gUw49B3oQsvwBA==",
      "dev": true,
      "engines": {
        "node": ">=4.0"
      }
    },
    "node_modules/estraverse": {
      "version": "4.3.0",
      "resolved": "https://registry.npmjs.org/estraverse/-/estraverse-4.3.0.tgz",
      "integrity": "sha512-39nnKffWz8xN1BU/2c79n9nB9HDzo0niYUqx6xyqUnyoAnQyyWpOTdZEeiCch8BBu515t4wp9ZmgVfVhn9EBpw==",
      "dev": true,
      "engines": {
        "node": ">=4.0"
      }
    },
    "node_modules/esutils": {
      "version": "2.0.3",
      "resolved": "https://registry.npmjs.org/esutils/-/esutils-2.0.3.tgz",
      "integrity": "sha512-kVscqXk4OCp68SZ0dkgEKVi6/8ij300KBWTJq32P/dYeWTSwK41WyTxalN1eRmA5Z9UU/LX9D7FWSmV9SAYx6g==",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/etag": {
      "version": "1.8.1",
      "resolved": "https://registry.npmjs.org/etag/-/etag-1.8.1.tgz",
      "integrity": "sha1-Qa4u62XvpiJorr/qg6x9eSmbCIc=",
      "engines": {
        "node": ">= 0.6"
      }
    },
    "node_modules/eventemitter-asyncresource": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/eventemitter-asyncresource/-/eventemitter-asyncresource-1.0.0.tgz",
      "integrity": "sha512-39F7TBIV0G7gTelxwbEqnwhp90eqCPON1k0NwNfwhgKn4Co4ybUbj2pECcXT0B3ztRKZ7Pw1JujUUgmQJHcVAQ==",
      "dev": true
    },
    "node_modules/eventemitter3": {
      "version": "4.0.7",
      "resolved": "https://registry.npmjs.org/eventemitter3/-/eventemitter3-4.0.7.tgz",
      "integrity": "sha512-8guHBZCwKnFhYdHr2ysuRWErTwhoN2X8XELRlrRwpmfeY2jjuUN4taQMsULKUVo1K4DvZl+0pgfyoysHxvmvEw==",
      "dev": true
    },
    "node_modules/events": {
      "version": "3.3.0",
      "resolved": "https://registry.npmjs.org/events/-/events-3.3.0.tgz",
      "integrity": "sha512-mQw+2fkQbALzQ7V0MY0IqdnXNOeTtP4r0lN9z7AAawCXgqea7bDii20AYrIBrFd/Hx0M2Ocz6S111CaFkUcb0Q==",
      "dev": true,
      "engines": {
        "node": ">=0.8.x"
      }
    },
    "node_modules/execa": {
      "version": "5.1.1",
      "resolved": "https://registry.npmjs.org/execa/-/execa-5.1.1.tgz",
      "integrity": "sha512-8uSpZZocAZRBAPIEINJj3Lo9HyGitllczc27Eh5YYojjMFMn8yHMDMaUHE2Jqfq05D/wucwI4JGURyXt1vchyg==",
      "dev": true,
      "dependencies": {
        "cross-spawn": "^7.0.3",
        "get-stream": "^6.0.0",
        "human-signals": "^2.1.0",
        "is-stream": "^2.0.0",
        "merge-stream": "^2.0.0",
        "npm-run-path": "^4.0.1",
        "onetime": "^5.1.2",
        "signal-exit": "^3.0.3",
        "strip-final-newline": "^2.0.0"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sindresorhus/execa?sponsor=1"
      }
    },
    "node_modules/express": {
      "version": "4.17.2",
      "resolved": "https://registry.npmjs.org/express/-/express-4.17.2.tgz",
      "integrity": "sha512-oxlxJxcQlYwqPWKVJJtvQiwHgosH/LrLSPA+H4UxpyvSS6jC5aH+5MoHFM+KABgTOt0APue4w66Ha8jCUo9QGg==",
      "dependencies": {
        "accepts": "~1.3.7",
        "array-flatten": "1.1.1",
        "body-parser": "1.19.1",
        "content-disposition": "0.5.4",
        "content-type": "~1.0.4",
        "cookie": "0.4.1",
        "cookie-signature": "1.0.6",
        "debug": "2.6.9",
        "depd": "~1.1.2",
        "encodeurl": "~1.0.2",
        "escape-html": "~1.0.3",
        "etag": "~1.8.1",
        "finalhandler": "~1.1.2",
        "fresh": "0.5.2",
        "merge-descriptors": "1.0.1",
        "methods": "~1.1.2",
        "on-finished": "~2.3.0",
        "parseurl": "~1.3.3",
        "path-to-regexp": "0.1.7",
        "proxy-addr": "~2.0.7",
        "qs": "6.9.6",
        "range-parser": "~1.2.1",
        "safe-buffer": "5.2.1",
        "send": "0.17.2",
        "serve-static": "1.14.2",
        "setprototypeof": "1.2.0",
        "statuses": "~1.5.0",
        "type-is": "~1.6.18",
        "utils-merge": "1.0.1",
        "vary": "~1.1.2"
      },
      "engines": {
        "node": ">= 0.10.0"
      }
    },
    "node_modules/express-urlrewrite": {
      "version": "1.4.0",
      "resolved": "https://registry.npmjs.org/express-urlrewrite/-/express-urlrewrite-1.4.0.tgz",
      "integrity": "sha512-PI5h8JuzoweS26vFizwQl6UTF25CAHSggNv0J25Dn/IKZscJHWZzPrI5z2Y2jgOzIaw2qh8l6+/jUcig23Z2SA==",
      "dependencies": {
        "debug": "*",
        "path-to-regexp": "^1.0.3"
      }
    },
    "node_modules/express-urlrewrite/node_modules/isarray": {
      "version": "0.0.1",
      "resolved": "https://registry.npmjs.org/isarray/-/isarray-0.0.1.tgz",
      "integrity": "sha1-ihis/Kmo9Bd+Cav8YDiTmwXR7t8="
    },
    "node_modules/express-urlrewrite/node_modules/path-to-regexp": {
      "version": "1.8.0",
      "resolved": "https://registry.npmjs.org/path-to-regexp/-/path-to-regexp-1.8.0.tgz",
      "integrity": "sha512-n43JRhlUKUAlibEJhPeir1ncUID16QnEjNpwzNdO3Lm4ywrBpBZ5oLD0I6br9evr1Y9JTqwRtAh7JLoOzAQdVA==",
      "dependencies": {
        "isarray": "0.0.1"
      }
    },
    "node_modules/express/node_modules/array-flatten": {
      "version": "1.1.1",
      "resolved": "https://registry.npmjs.org/array-flatten/-/array-flatten-1.1.1.tgz",
      "integrity": "sha1-ml9pkFGx5wczKPKgCJaLZOopVdI="
    },
    "node_modules/express/node_modules/debug": {
      "version": "2.6.9",
      "resolved": "https://registry.npmjs.org/debug/-/debug-2.6.9.tgz",
      "integrity": "sha512-bC7ElrdJaJnPbAP+1EotYvqZsb3ecl5wi6Bfi6BJTUcNowp6cvspg0jXznRTKDjm/E7AdgFBVeAPVMNcKGsHMA==",
      "dependencies": {
        "ms": "2.0.0"
      }
    },
    "node_modules/express/node_modules/ms": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/ms/-/ms-2.0.0.tgz",
      "integrity": "sha1-VgiurfwAvmwpAd9fmGF4jeDVl8g="
    },
    "node_modules/express/node_modules/safe-buffer": {
      "version": "5.2.1",
      "resolved": "https://registry.npmjs.org/safe-buffer/-/safe-buffer-5.2.1.tgz",
      "integrity": "sha512-rp3So07KcdmmKbGvgaNxQSJr7bGVSVk5S9Eq1F+ppbRo70+YeaDxkw5Dd8NPN+GD6bjnYm2VuPuCXmpuYvmCXQ==",
      "funding": [
        {
          "type": "github",
          "url": "https://github.com/sponsors/feross"
        },
        {
          "type": "patreon",
          "url": "https://www.patreon.com/feross"
        },
        {
          "type": "consulting",
          "url": "https://feross.org/support"
        }
      ]
    },
    "node_modules/extend": {
      "version": "3.0.2",
      "resolved": "https://registry.npmjs.org/extend/-/extend-3.0.2.tgz",
      "integrity": "sha512-fjquC59cD7CyW6urNXK0FBufkZcoiGG80wTuPujX590cB5Ttln20E2UB4S/WARVqhXffZl2LNgS+gQdPIIim/g==",
      "dev": true
    },
    "node_modules/external-editor": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/external-editor/-/external-editor-3.1.0.tgz",
      "integrity": "sha512-hMQ4CX1p1izmuLYyZqLMO/qGNw10wSv9QDCPfzXfyFrOaCSSoRfqE1Kf1s5an66J5JZC62NewG+mK49jOCtQew==",
      "dev": true,
      "dependencies": {
        "chardet": "^0.7.0",
        "iconv-lite": "^0.4.24",
        "tmp": "^0.0.33"
      },
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/fast-deep-equal": {
      "version": "3.1.3",
      "resolved": "https://registry.npmjs.org/fast-deep-equal/-/fast-deep-equal-3.1.3.tgz",
      "integrity": "sha512-f3qQ9oQy9j2AhBe/H9VC91wLmKBCCU/gDOnKNAYG5hswO7BLKj09Hc5HYNz9cGI++xlpDCIgDaitVs03ATR84Q==",
      "dev": true
    },
    "node_modules/fast-glob": {
      "version": "3.2.11",
      "resolved": "https://registry.npmjs.org/fast-glob/-/fast-glob-3.2.11.tgz",
      "integrity": "sha512-xrO3+1bxSo3ZVHAnqzyuewYT6aMFHRAd4Kcs92MAonjwQZLsK9d0SF1IyQ3k5PoirxTW0Oe/RqFgMQ6TcNE5Ew==",
      "dev": true,
      "dependencies": {
        "@nodelib/fs.stat": "^2.0.2",
        "@nodelib/fs.walk": "^1.2.3",
        "glob-parent": "^5.1.2",
        "merge2": "^1.3.0",
        "micromatch": "^4.0.4"
      },
      "engines": {
        "node": ">=8.6.0"
      }
    },
    "node_modules/fast-json-stable-stringify": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/fast-json-stable-stringify/-/fast-json-stable-stringify-2.1.0.tgz",
      "integrity": "sha512-lhd/wF+Lk98HZoTCtlVraHtfh5XYijIjalXck7saUtuanSDyLMxnHhSXEDJqHxD7msR8D0uCmqlkwjCV8xvwHw==",
      "dev": true
    },
    "node_modules/fastq": {
      "version": "1.13.0",
      "resolved": "https://registry.npmjs.org/fastq/-/fastq-1.13.0.tgz",
      "integrity": "sha512-YpkpUnK8od0o1hmeSc7UUs/eB/vIPWJYjKck2QKIzAf71Vm1AAQ3EbuZB3g2JIy+pg+ERD0vqI79KyZiB2e2Nw==",
      "dev": true,
      "dependencies": {
        "reusify": "^1.0.4"
      }
    },
    "node_modules/faye-websocket": {
      "version": "0.11.4",
      "resolved": "https://registry.npmjs.org/faye-websocket/-/faye-websocket-0.11.4.tgz",
      "integrity": "sha512-CzbClwlXAuiRQAlUyfqPgvPoNKTckTPGfwZV4ZdAhVcP2lh9KUxJg2b5GkE7XbjKQ3YJnQ9z6D9ntLAlB+tP8g==",
      "dev": true,
      "dependencies": {
        "websocket-driver": ">=0.5.1"
      },
      "engines": {
        "node": ">=0.8.0"
      }
    },
    "node_modules/figures": {
      "version": "3.2.0",
      "resolved": "https://registry.npmjs.org/figures/-/figures-3.2.0.tgz",
      "integrity": "sha512-yaduQFRKLXYOGgEn6AZau90j3ggSOyiqXU0F9JZfeXYhNa+Jk4X+s45A2zg5jns87GAFa34BBm2kXw4XpNcbdg==",
      "dev": true,
      "dependencies": {
        "escape-string-regexp": "^1.0.5"
      },
      "engines": {
        "node": ">=8"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/fill-range": {
      "version": "7.0.1",
      "resolved": "https://registry.npmjs.org/fill-range/-/fill-range-7.0.1.tgz",
      "integrity": "sha512-qOo9F+dMUmC2Lcb4BbVvnKJxTPjCm+RRpe4gDuGrzkL7mEVl/djYSu2OdQ2Pa302N4oqkSg9ir6jaLWJ2USVpQ==",
      "dev": true,
      "dependencies": {
        "to-regex-range": "^5.0.1"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/finalhandler": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/finalhandler/-/finalhandler-1.1.2.tgz",
      "integrity": "sha512-aAWcW57uxVNrQZqFXjITpW3sIUQmHGG3qSb9mUah9MgMC4NeWhNOlNjXEYq3HjRAvL6arUviZGGJsBg6z0zsWA==",
      "dependencies": {
        "debug": "2.6.9",
        "encodeurl": "~1.0.2",
        "escape-html": "~1.0.3",
        "on-finished": "~2.3.0",
        "parseurl": "~1.3.3",
        "statuses": "~1.5.0",
        "unpipe": "~1.0.0"
      },
      "engines": {
        "node": ">= 0.8"
      }
    },
    "node_modules/finalhandler/node_modules/debug": {
      "version": "2.6.9",
      "resolved": "https://registry.npmjs.org/debug/-/debug-2.6.9.tgz",
      "integrity": "sha512-bC7ElrdJaJnPbAP+1EotYvqZsb3ecl5wi6Bfi6BJTUcNowp6cvspg0jXznRTKDjm/E7AdgFBVeAPVMNcKGsHMA==",
      "dependencies": {
        "ms": "2.0.0"
      }
    },
    "node_modules/finalhandler/node_modules/ms": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/ms/-/ms-2.0.0.tgz",
      "integrity": "sha1-VgiurfwAvmwpAd9fmGF4jeDVl8g="
    },
    "node_modules/find-cache-dir": {
      "version": "3.3.2",
      "resolved": "https://registry.npmjs.org/find-cache-dir/-/find-cache-dir-3.3.2.tgz",
      "integrity": "sha512-wXZV5emFEjrridIgED11OoUKLxiYjAcqot/NJdAkOhlJ+vGzwhOAfcG5OX1jP+S0PcjEn8bdMJv+g2jwQ3Onig==",
      "dev": true,
      "dependencies": {
        "commondir": "^1.0.1",
        "make-dir": "^3.0.2",
        "pkg-dir": "^4.1.0"
      },
      "engines": {
        "node": ">=8"
      },
      "funding": {
        "url": "https://github.com/avajs/find-cache-dir?sponsor=1"
      }
    },
    "node_modules/find-up": {
      "version": "4.1.0",
      "resolved": "https://registry.npmjs.org/find-up/-/find-up-4.1.0.tgz",
      "integrity": "sha512-PpOwAdQ/YlXQ2vj8a3h8IipDuYRi3wceVQQGYWxNINccq40Anw7BlsEXCMbt1Zt+OLA6Fq9suIpIWD0OsnISlw==",
      "dev": true,
      "dependencies": {
        "locate-path": "^5.0.0",
        "path-exists": "^4.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/flatted": {
      "version": "3.2.5",
      "resolved": "https://registry.npmjs.org/flatted/-/flatted-3.2.5.tgz",
      "integrity": "sha512-WIWGi2L3DyTUvUrwRKgGi9TwxQMUEqPOPQBVi71R96jZXJdFskXEmf54BoZaS1kknGODoIGASGEzBUYdyMCBJg==",
      "dev": true
    },
    "node_modules/follow-redirects": {
      "version": "1.14.7",
      "resolved": "https://registry.npmjs.org/follow-redirects/-/follow-redirects-1.14.7.tgz",
      "integrity": "sha512-+hbxoLbFMbRKDwohX8GkTataGqO6Jb7jGwpAlwgy2bIz25XtRm7KEzJM76R1WiNT5SwZkX4Y75SwBolkpmE7iQ==",
      "dev": true,
      "funding": [
        {
          "type": "individual",
          "url": "https://github.com/sponsors/RubenVerborgh"
        }
      ],
      "engines": {
        "node": ">=4.0"
      },
      "peerDependenciesMeta": {
        "debug": {
          "optional": true
        }
      }
    },
    "node_modules/forwarded": {
      "version": "0.2.0",
      "resolved": "https://registry.npmjs.org/forwarded/-/forwarded-0.2.0.tgz",
      "integrity": "sha512-buRG0fpBtRHSTCOASe6hD258tEubFoRLb4ZNA6NxMVHNw2gOcwHo9wyablzMzOA5z9xA9L1KNjk/Nt6MT9aYow==",
      "engines": {
        "node": ">= 0.6"
      }
    },
    "node_modules/fraction.js": {
      "version": "4.1.2",
      "resolved": "https://registry.npmjs.org/fraction.js/-/fraction.js-4.1.2.tgz",
      "integrity": "sha512-o2RiJQ6DZaR/5+Si0qJUIy637QMRudSi9kU/FFzx9EZazrIdnBgpU+3sEWCxAVhH2RtxW2Oz+T4p2o8uOPVcgA==",
      "dev": true,
      "engines": {
        "node": "*"
      },
      "funding": {
        "type": "patreon",
        "url": "https://www.patreon.com/infusion"
      }
    },
    "node_modules/fresh": {
      "version": "0.5.2",
      "resolved": "https://registry.npmjs.org/fresh/-/fresh-0.5.2.tgz",
      "integrity": "sha1-PYyt2Q2XZWn6g1qx+OSyOhBWBac=",
      "engines": {
        "node": ">= 0.6"
      }
    },
    "node_modules/fs-extra": {
      "version": "10.0.0",
      "resolved": "https://registry.npmjs.org/fs-extra/-/fs-extra-10.0.0.tgz",
      "integrity": "sha512-C5owb14u9eJwizKGdchcDUQeFtlSHHthBk8pbX9Vc1PFZrLombudjDnNns88aYslCyF6IY5SUw3Roz6xShcEIQ==",
      "dev": true,
      "dependencies": {
        "graceful-fs": "^4.2.0",
        "jsonfile": "^6.0.1",
        "universalify": "^2.0.0"
      },
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/fs-minipass": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/fs-minipass/-/fs-minipass-2.1.0.tgz",
      "integrity": "sha512-V/JgOLFCS+R6Vcq0slCuaeWEdNC3ouDlJMNIsacH2VtALiu9mV4LPrHc5cDl8k5aw6J8jwgWWpiTo5RYhmIzvg==",
      "dev": true,
      "dependencies": {
        "minipass": "^3.0.0"
      },
      "engines": {
        "node": ">= 8"
      }
    },
    "node_modules/fs-monkey": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/fs-monkey/-/fs-monkey-1.0.3.tgz",
      "integrity": "sha512-cybjIfiiE+pTWicSCLFHSrXZ6EilF30oh91FDP9S2B051prEa7QWfrVTQm10/dDpswBDXZugPa1Ogu8Yh+HV0Q==",
      "dev": true
    },
    "node_modules/fs.realpath": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/fs.realpath/-/fs.realpath-1.0.0.tgz",
      "integrity": "sha1-FQStJSMVjKpA20onh8sBQRmU6k8=",
      "dev": true
    },
    "node_modules/fsevents": {
      "version": "2.3.2",
      "resolved": "https://registry.npmjs.org/fsevents/-/fsevents-2.3.2.tgz",
      "integrity": "sha512-xiqMQR4xAeHTuB9uWm+fFRcIOgKBMiOBP+eXiyT7jsgVCq1bkVygt00oASowB7EdtpOHaaPgKt812P9ab+DDKA==",
      "dev": true,
      "hasInstallScript": true,
      "optional": true,
      "os": [
        "darwin"
      ],
      "engines": {
        "node": "^8.16.0 || ^10.6.0 || >=11.0.0"
      }
    },
    "node_modules/function-bind": {
      "version": "1.1.1",
      "resolved": "https://registry.npmjs.org/function-bind/-/function-bind-1.1.1.tgz",
      "integrity": "sha512-yIovAzMX49sF8Yl58fSCWJ5svSLuaibPxXQJFLmBObTuCr0Mf1KiPopGM9NiFjiYBCbfaa2Fh6breQ6ANVTI0A==",
      "dev": true
    },
    "node_modules/gauge": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/gauge/-/gauge-4.0.0.tgz",
      "integrity": "sha512-F8sU45yQpjQjxKkm1UOAhf0U/O0aFt//Fl7hsrNVto+patMHjs7dPI9mFOGUKbhrgKm0S3EjW3scMFuQmWSROw==",
      "dev": true,
      "dependencies": {
        "ansi-regex": "^5.0.1",
        "aproba": "^1.0.3 || ^2.0.0",
        "color-support": "^1.1.2",
        "console-control-strings": "^1.0.0",
        "has-unicode": "^2.0.1",
        "signal-exit": "^3.0.0",
        "string-width": "^4.2.3",
        "strip-ansi": "^6.0.1",
        "wide-align": "^1.1.2"
      },
      "engines": {
        "node": "^12.13.0 || ^14.15.0 || >=16"
      }
    },
    "node_modules/gensync": {
      "version": "1.0.0-beta.2",
      "resolved": "https://registry.npmjs.org/gensync/-/gensync-1.0.0-beta.2.tgz",
      "integrity": "sha512-3hN7NaskYvMDLQY55gnW3NQ+mesEAepTqlg+VEbj7zzqEMBVNhzcGYYeqFo/TlYz6eQiFcp1HcsCZO+nGgS8zg==",
      "dev": true,
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/get-caller-file": {
      "version": "2.0.5",
      "resolved": "https://registry.npmjs.org/get-caller-file/-/get-caller-file-2.0.5.tgz",
      "integrity": "sha512-DyFP3BM/3YHTQOCUL/w0OZHR0lpKeGrxotcHWcqNEdnltqFwXVfhEBQ94eIo34AfQpo0rGki4cyIiftY06h2Fg==",
      "engines": {
        "node": "6.* || 8.* || >= 10.*"
      }
    },
    "node_modules/get-intrinsic": {
      "version": "1.1.1",
      "resolved": "https://registry.npmjs.org/get-intrinsic/-/get-intrinsic-1.1.1.tgz",
      "integrity": "sha512-kWZrnVM42QCiEA2Ig1bG8zjoIMOgxWwYCEeNdwY6Tv/cOSeGpcoX4pXHfKUxNKVoArnrEr2e9srnAxxGIraS9Q==",
      "dev": true,
      "dependencies": {
        "function-bind": "^1.1.1",
        "has": "^1.0.3",
        "has-symbols": "^1.0.1"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/get-package-type": {
      "version": "0.1.0",
      "resolved": "https://registry.npmjs.org/get-package-type/-/get-package-type-0.1.0.tgz",
      "integrity": "sha512-pjzuKtY64GYfWizNAJ0fr9VqttZkNiK2iS430LtIHzjBEr6bX8Am2zm4sW4Ro5wjWW5cAlRL1qAMTcXbjNAO2Q==",
      "dev": true,
      "engines": {
        "node": ">=8.0.0"
      }
    },
    "node_modules/get-stream": {
      "version": "6.0.1",
      "resolved": "https://registry.npmjs.org/get-stream/-/get-stream-6.0.1.tgz",
      "integrity": "sha512-ts6Wi+2j3jQjqi70w5AlN8DFnkSwC+MqmxEzdEALB2qXZYV3X/b1CTfgPLGJNMeAWxdPfU8FO1ms3NUfaHCPYg==",
      "dev": true,
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/glob": {
      "version": "7.2.0",
      "resolved": "https://registry.npmjs.org/glob/-/glob-7.2.0.tgz",
      "integrity": "sha512-lmLf6gtyrPq8tTjSmrO94wBeQbFR3HbLHbuyD69wuyQkImp2hWqMGB47OX65FBkPffO641IP9jWa1z4ivqG26Q==",
      "dev": true,
      "dependencies": {
        "fs.realpath": "^1.0.0",
        "inflight": "^1.0.4",
        "inherits": "2",
        "minimatch": "^3.0.4",
        "once": "^1.3.0",
        "path-is-absolute": "^1.0.0"
      },
      "engines": {
        "node": "*"
      },
      "funding": {
        "url": "https://github.com/sponsors/isaacs"
      }
    },
    "node_modules/glob-parent": {
      "version": "5.1.2",
      "resolved": "https://registry.npmjs.org/glob-parent/-/glob-parent-5.1.2.tgz",
      "integrity": "sha512-AOIgSQCepiJYwP3ARnGx+5VnTu2HBYdzbGP45eLw1vr3zB3vZLeyed1sC9hnbcOc9/SrMyM5RPQrkGz4aS9Zow==",
      "dev": true,
      "dependencies": {
        "is-glob": "^4.0.1"
      },
      "engines": {
        "node": ">= 6"
      }
    },
    "node_modules/glob-to-regexp": {
      "version": "0.4.1",
      "resolved": "https://registry.npmjs.org/glob-to-regexp/-/glob-to-regexp-0.4.1.tgz",
      "integrity": "sha512-lkX1HJXwyMcprw/5YUZc2s7DrpAiHB21/V+E1rHUrVNokkvB6bqMzT0VfV6/86ZNabt1k14YOIaT7nDvOX3Iiw==",
      "dev": true
    },
    "node_modules/global-dirs": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/global-dirs/-/global-dirs-3.0.0.tgz",
      "integrity": "sha512-v8ho2DS5RiCjftj1nD9NmnfaOzTdud7RRnVd9kFNOjqZbISlx5DQ+OrTkywgd0dIt7oFCvKetZSHoHcP3sDdiA==",
      "dependencies": {
        "ini": "2.0.0"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/globals": {
      "version": "11.12.0",
      "resolved": "https://registry.npmjs.org/globals/-/globals-11.12.0.tgz",
      "integrity": "sha512-WOBp/EEGUiIsJSp7wcv/y6MO+lV9UoncWqxuFfm8eBwzWNgyfBd6Gz+IeKQ9jCmyhoH99g15M3T+QaVHFjizVA==",
      "dev": true,
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/globby": {
      "version": "12.2.0",
      "resolved": "https://registry.npmjs.org/globby/-/globby-12.2.0.tgz",
      "integrity": "sha512-wiSuFQLZ+urS9x2gGPl1H5drc5twabmm4m2gTR27XDFyjUHJUNsS8o/2aKyIF6IoBaR630atdher0XJ5g6OMmA==",
      "dev": true,
      "dependencies": {
        "array-union": "^3.0.1",
        "dir-glob": "^3.0.1",
        "fast-glob": "^3.2.7",
        "ignore": "^5.1.9",
        "merge2": "^1.4.1",
        "slash": "^4.0.0"
      },
      "engines": {
        "node": "^12.20.0 || ^14.13.1 || >=16.0.0"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/got": {
      "version": "9.6.0",
      "resolved": "https://registry.npmjs.org/got/-/got-9.6.0.tgz",
      "integrity": "sha512-R7eWptXuGYxwijs0eV+v3o6+XH1IqVK8dJOEecQfTmkncw9AV4dcw/Dhxi8MdlqPthxxpZyizMzyg8RTmEsG+Q==",
      "dependencies": {
        "@sindresorhus/is": "^0.14.0",
        "@szmarczak/http-timer": "^1.1.2",
        "cacheable-request": "^6.0.0",
        "decompress-response": "^3.3.0",
        "duplexer3": "^0.1.4",
        "get-stream": "^4.1.0",
        "lowercase-keys": "^1.0.1",
        "mimic-response": "^1.0.1",
        "p-cancelable": "^1.0.0",
        "to-readable-stream": "^1.0.0",
        "url-parse-lax": "^3.0.0"
      },
      "engines": {
        "node": ">=8.6"
      }
    },
    "node_modules/got/node_modules/get-stream": {
      "version": "4.1.0",
      "resolved": "https://registry.npmjs.org/get-stream/-/get-stream-4.1.0.tgz",
      "integrity": "sha512-GMat4EJ5161kIy2HevLlr4luNjBgvmj413KaQA7jt4V8B4RDsfpHk7WQ9GVqfYyyx8OS/L66Kox+rJRNklLK7w==",
      "dependencies": {
        "pump": "^3.0.0"
      },
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/graceful-fs": {
      "version": "4.2.9",
      "resolved": "https://registry.npmjs.org/graceful-fs/-/graceful-fs-4.2.9.tgz",
      "integrity": "sha512-NtNxqUcXgpW2iMrfqSfR73Glt39K+BLwWsPs94yR63v45T0Wbej7eRmL5cWfwEgqXnmjQp3zaJTshdRW/qC2ZQ=="
    },
    "node_modules/handle-thing": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/handle-thing/-/handle-thing-2.0.1.tgz",
      "integrity": "sha512-9Qn4yBxelxoh2Ow62nP+Ka/kMnOXRi8BXnRaUwezLNhqelnN49xKz4F/dPP8OYLxLxq6JDtZb2i9XznUQbNPTg==",
      "dev": true
    },
    "node_modules/has": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/has/-/has-1.0.3.tgz",
      "integrity": "sha512-f2dvO0VU6Oej7RkWJGrehjbzMAjFp5/VKPp5tTpWIV4JHHZK1/BxbFRtf/siA2SWTe09caDmVtYYzWEIbBS4zw==",
      "dev": true,
      "dependencies": {
        "function-bind": "^1.1.1"
      },
      "engines": {
        "node": ">= 0.4.0"
      }
    },
    "node_modules/has-flag": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/has-flag/-/has-flag-3.0.0.tgz",
      "integrity": "sha1-tdRU3CGZriJWmfNGfloH87lVuv0=",
      "dev": true,
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/has-symbols": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/has-symbols/-/has-symbols-1.0.2.tgz",
      "integrity": "sha512-chXa79rL/UC2KlX17jo3vRGz0azaWEx5tGqZg5pO3NUyEJVB17dMruQlzCCOfUvElghKcm5194+BCRvi2Rv/Gw==",
      "dev": true,
      "engines": {
        "node": ">= 0.4"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/has-tostringtag": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/has-tostringtag/-/has-tostringtag-1.0.0.tgz",
      "integrity": "sha512-kFjcSNhnlGV1kyoGk7OXKSawH5JOb/LzUc5w9B02hOTO0dfFRjbHQKvg1d6cf3HbeUmtU9VbbV3qzZ2Teh97WQ==",
      "dev": true,
      "dependencies": {
        "has-symbols": "^1.0.2"
      },
      "engines": {
        "node": ">= 0.4"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/has-unicode": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/has-unicode/-/has-unicode-2.0.1.tgz",
      "integrity": "sha1-4Ob+aijPUROIVeCG0Wkedx3iqLk=",
      "dev": true
    },
    "node_modules/has-yarn": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/has-yarn/-/has-yarn-2.1.0.tgz",
      "integrity": "sha512-UqBRqi4ju7T+TqGNdqAO0PaSVGsDGJUBQvk9eUWNGRY1CFGDzYhLWoM7JQEemnlvVcv/YEmc2wNW8BC24EnUsw==",
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/hdr-histogram-js": {
      "version": "2.0.3",
      "resolved": "https://registry.npmjs.org/hdr-histogram-js/-/hdr-histogram-js-2.0.3.tgz",
      "integrity": "sha512-Hkn78wwzWHNCp2uarhzQ2SGFLU3JY8SBDDd3TAABK4fc30wm+MuPOrg5QVFVfkKOQd6Bfz3ukJEI+q9sXEkK1g==",
      "dev": true,
      "dependencies": {
        "@assemblyscript/loader": "^0.10.1",
        "base64-js": "^1.2.0",
        "pako": "^1.0.3"
      }
    },
    "node_modules/hdr-histogram-percentiles-obj": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/hdr-histogram-percentiles-obj/-/hdr-histogram-percentiles-obj-3.0.0.tgz",
      "integrity": "sha512-7kIufnBqdsBGcSZLPJwqHT3yhk1QTsSlFsVD3kx5ixH/AlgBs9yM1q6DPhXZ8f8gtdqgh7N7/5btRLpQsS2gHw==",
      "dev": true
    },
    "node_modules/hosted-git-info": {
      "version": "4.1.0",
      "resolved": "https://registry.npmjs.org/hosted-git-info/-/hosted-git-info-4.1.0.tgz",
      "integrity": "sha512-kyCuEOWjJqZuDbRHzL8V93NzQhwIB71oFWSyzVo+KPZI+pnQPPxucdkrOZvkLRnrf5URsQM+IJ09Dw29cRALIA==",
      "dev": true,
      "dependencies": {
        "lru-cache": "^6.0.0"
      },
      "engines": {
        "node": ">=10"
      }
    },
    "node_modules/hpack.js": {
      "version": "2.1.6",
      "resolved": "https://registry.npmjs.org/hpack.js/-/hpack.js-2.1.6.tgz",
      "integrity": "sha1-h3dMCUnlE/QuhFdbPEVoH63ioLI=",
      "dev": true,
      "dependencies": {
        "inherits": "^2.0.1",
        "obuf": "^1.0.0",
        "readable-stream": "^2.0.1",
        "wbuf": "^1.1.0"
      }
    },
    "node_modules/hpack.js/node_modules/readable-stream": {
      "version": "2.3.7",
      "resolved": "https://registry.npmjs.org/readable-stream/-/readable-stream-2.3.7.tgz",
      "integrity": "sha512-Ebho8K4jIbHAxnuxi7o42OrZgF/ZTNcsZj6nRKyUmkhLFq8CHItp/fy6hQZuZmP/n3yZ9VBUbp4zz/mX8hmYPw==",
      "dev": true,
      "dependencies": {
        "core-util-is": "~1.0.0",
        "inherits": "~2.0.3",
        "isarray": "~1.0.0",
        "process-nextick-args": "~2.0.0",
        "safe-buffer": "~5.1.1",
        "string_decoder": "~1.1.1",
        "util-deprecate": "~1.0.1"
      }
    },
    "node_modules/hpack.js/node_modules/string_decoder": {
      "version": "1.1.1",
      "resolved": "https://registry.npmjs.org/string_decoder/-/string_decoder-1.1.1.tgz",
      "integrity": "sha512-n/ShnvDi6FHbbVfviro+WojiFzv+s8MPMHBczVePfUpDJLwoLT0ht1l4YwBCbi8pJAveEEdnkHyPyTP/mzRfwg==",
      "dev": true,
      "dependencies": {
        "safe-buffer": "~5.1.0"
      }
    },
    "node_modules/html-entities": {
      "version": "2.3.2",
      "resolved": "https://registry.npmjs.org/html-entities/-/html-entities-2.3.2.tgz",
      "integrity": "sha512-c3Ab/url5ksaT0WyleslpBEthOzWhrjQbg75y7XUsfSzi3Dgzt0l8w5e7DylRn15MTlMMD58dTfzddNS2kcAjQ==",
      "dev": true
    },
    "node_modules/html-escaper": {
      "version": "2.0.2",
      "resolved": "https://registry.npmjs.org/html-escaper/-/html-escaper-2.0.2.tgz",
      "integrity": "sha512-H2iMtd0I4Mt5eYiapRdIDjp+XzelXQ0tFE4JS7YFwFevXXMmOp9myNrUvCg0D6ws8iqkRPBfKHgbwig1SmlLfg==",
      "dev": true
    },
    "node_modules/http-cache-semantics": {
      "version": "4.1.0",
      "resolved": "https://registry.npmjs.org/http-cache-semantics/-/http-cache-semantics-4.1.0.tgz",
      "integrity": "sha512-carPklcUh7ROWRK7Cv27RPtdhYhUsela/ue5/jKzjegVvXDqM2ILE9Q2BGn9JZJh1g87cp56su/FgQSzcWS8cQ=="
    },
    "node_modules/http-deceiver": {
      "version": "1.2.7",
      "resolved": "https://registry.npmjs.org/http-deceiver/-/http-deceiver-1.2.7.tgz",
      "integrity": "sha1-+nFolEq5pRnTN8sL7HKE3D5yPYc=",
      "dev": true
    },
    "node_modules/http-errors": {
      "version": "1.8.1",
      "resolved": "https://registry.npmjs.org/http-errors/-/http-errors-1.8.1.tgz",
      "integrity": "sha512-Kpk9Sm7NmI+RHhnj6OIWDI1d6fIoFAtFt9RLaTMRlg/8w49juAStsrBgp0Dp4OdxdVbRIeKhtCUvoi/RuAhO4g==",
      "dependencies": {
        "depd": "~1.1.2",
        "inherits": "2.0.4",
        "setprototypeof": "1.2.0",
        "statuses": ">= 1.5.0 < 2",
        "toidentifier": "1.0.1"
      },
      "engines": {
        "node": ">= 0.6"
      }
    },
    "node_modules/http-parser-js": {
      "version": "0.5.5",
      "resolved": "https://registry.npmjs.org/http-parser-js/-/http-parser-js-0.5.5.tgz",
      "integrity": "sha512-x+JVEkO2PoM8qqpbPbOL3cqHPwerep7OwzK7Ay+sMQjKzaKCqWvjoXm5tqMP9tXWWTnTzAjIhXg+J99XYuPhPA==",
      "dev": true
    },
    "node_modules/http-proxy": {
      "version": "1.18.1",
      "resolved": "https://registry.npmjs.org/http-proxy/-/http-proxy-1.18.1.tgz",
      "integrity": "sha512-7mz/721AbnJwIVbnaSv1Cz3Am0ZLT/UBwkC92VlxhXv/k/BBQfM2fXElQNC27BVGr0uwUpplYPQM9LnaBMR5NQ==",
      "dev": true,
      "dependencies": {
        "eventemitter3": "^4.0.0",
        "follow-redirects": "^1.0.0",
        "requires-port": "^1.0.0"
      },
      "engines": {
        "node": ">=8.0.0"
      }
    },
    "node_modules/http-proxy-agent": {
      "version": "4.0.1",
      "resolved": "https://registry.npmjs.org/http-proxy-agent/-/http-proxy-agent-4.0.1.tgz",
      "integrity": "sha512-k0zdNgqWTGA6aeIRVpvfVob4fL52dTfaehylg0Y4UvSySvOq/Y+BOyPrgpUrA7HylqvU8vIZGsRuXmspskV0Tg==",
      "dev": true,
      "dependencies": {
        "@tootallnate/once": "1",
        "agent-base": "6",
        "debug": "4"
      },
      "engines": {
        "node": ">= 6"
      }
    },
    "node_modules/http-proxy-middleware": {
      "version": "2.0.2",
      "resolved": "https://registry.npmjs.org/http-proxy-middleware/-/http-proxy-middleware-2.0.2.tgz",
      "integrity": "sha512-XtmDN5w+vdFTBZaYhdJAbMqn0DP/EhkUaAeo963mojwpKMMbw6nivtFKw07D7DDOH745L5k0VL0P8KRYNEVF/g==",
      "dev": true,
      "dependencies": {
        "@types/http-proxy": "^1.17.8",
        "http-proxy": "^1.18.1",
        "is-glob": "^4.0.1",
        "is-plain-obj": "^3.0.0",
        "micromatch": "^4.0.2"
      },
      "engines": {
        "node": ">=12.0.0"
      },
      "peerDependencies": {
        "@types/express": "^4.17.13"
      }
    },
    "node_modules/https-proxy-agent": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/https-proxy-agent/-/https-proxy-agent-5.0.0.tgz",
      "integrity": "sha512-EkYm5BcKUGiduxzSt3Eppko+PiNWNEpa4ySk9vTC6wDsQJW9rHSa+UhGNJoRYp7bz6Ht1eaRIa6QaJqO5rCFbA==",
      "dev": true,
      "dependencies": {
        "agent-base": "6",
        "debug": "4"
      },
      "engines": {
        "node": ">= 6"
      }
    },
    "node_modules/human-signals": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/human-signals/-/human-signals-2.1.0.tgz",
      "integrity": "sha512-B4FFZ6q/T2jhhksgkbEW3HBvWIfDW85snkQgawt07S7J5QXTk6BkNV+0yAeZrM5QpMAdYlocGoljn0sJ/WQkFw==",
      "dev": true,
      "engines": {
        "node": ">=10.17.0"
      }
    },
    "node_modules/humanize-ms": {
      "version": "1.2.1",
      "resolved": "https://registry.npmjs.org/humanize-ms/-/humanize-ms-1.2.1.tgz",
      "integrity": "sha1-xG4xWaKT9riW2ikxbYtv6Lt5u+0=",
      "dev": true,
      "dependencies": {
        "ms": "^2.0.0"
      }
    },
    "node_modules/iconv-lite": {
      "version": "0.4.24",
      "resolved": "https://registry.npmjs.org/iconv-lite/-/iconv-lite-0.4.24.tgz",
      "integrity": "sha512-v3MXnZAcvnywkTUEZomIActle7RXXeedOR31wwl7VlyoXO4Qi9arvSenNQWne1TcRwhCL1HwLI21bEqdpj8/rA==",
      "dependencies": {
        "safer-buffer": ">= 2.1.2 < 3"
      },
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/icss-utils": {
      "version": "5.1.0",
      "resolved": "https://registry.npmjs.org/icss-utils/-/icss-utils-5.1.0.tgz",
      "integrity": "sha512-soFhflCVWLfRNOPU3iv5Z9VUdT44xFRbzjLsEzSr5AQmgqPMTHdU3PMT1Cf1ssx8fLNJDA1juftYl+PUcv3MqA==",
      "dev": true,
      "engines": {
        "node": "^10 || ^12 || >= 14"
      },
      "peerDependencies": {
        "postcss": "^8.1.0"
      }
    },
    "node_modules/ieee754": {
      "version": "1.2.1",
      "resolved": "https://registry.npmjs.org/ieee754/-/ieee754-1.2.1.tgz",
      "integrity": "sha512-dcyqhDvX1C46lXZcVqCpK+FtMRQVdIMN6/Df5js2zouUsqG7I6sFxitIC+7KYK29KdXOLHdu9zL4sFnoVQnqaA==",
      "dev": true,
      "funding": [
        {
          "type": "github",
          "url": "https://github.com/sponsors/feross"
        },
        {
          "type": "patreon",
          "url": "https://www.patreon.com/feross"
        },
        {
          "type": "consulting",
          "url": "https://feross.org/support"
        }
      ]
    },
    "node_modules/ignore": {
      "version": "5.2.0",
      "resolved": "https://registry.npmjs.org/ignore/-/ignore-5.2.0.tgz",
      "integrity": "sha512-CmxgYGiEPCLhfLnpPp1MoRmifwEIOgjcHXxOBjv7mY96c+eWScsOP9c112ZyLdWHi0FxHjI+4uVhKYp/gcdRmQ==",
      "dev": true,
      "engines": {
        "node": ">= 4"
      }
    },
    "node_modules/ignore-walk": {
      "version": "4.0.1",
      "resolved": "https://registry.npmjs.org/ignore-walk/-/ignore-walk-4.0.1.tgz",
      "integrity": "sha512-rzDQLaW4jQbh2YrOFlJdCtX8qgJTehFRYiUB2r1osqTeDzV/3+Jh8fz1oAPzUThf3iku8Ds4IDqawI5d8mUiQw==",
      "dev": true,
      "dependencies": {
        "minimatch": "^3.0.4"
      },
      "engines": {
        "node": ">=10"
      }
    },
    "node_modules/image-size": {
      "version": "0.5.5",
      "resolved": "https://registry.npmjs.org/image-size/-/image-size-0.5.5.tgz",
      "integrity": "sha1-Cd/Uq50g4p6xw+gLiZA3jfnjy5w=",
      "dev": true,
      "optional": true,
      "bin": {
        "image-size": "bin/image-size.js"
      },
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/immutable": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/immutable/-/immutable-4.0.0.tgz",
      "integrity": "sha512-zIE9hX70qew5qTUjSS7wi1iwj/l7+m54KWU247nhM3v806UdGj1yDndXj+IOYxxtW9zyLI+xqFNZjTuDaLUqFw==",
      "dev": true
    },
    "node_modules/import-fresh": {
      "version": "3.3.0",
      "resolved": "https://registry.npmjs.org/import-fresh/-/import-fresh-3.3.0.tgz",
      "integrity": "sha512-veYYhQa+D1QBKznvhUHxb8faxlrwUnxseDAbAp457E0wLNio2bOSKnjYDhMj+YiAq61xrMGhQk9iXVk5FzgQMw==",
      "dev": true,
      "dependencies": {
        "parent-module": "^1.0.0",
        "resolve-from": "^4.0.0"
      },
      "engines": {
        "node": ">=6"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/import-fresh/node_modules/resolve-from": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/resolve-from/-/resolve-from-4.0.0.tgz",
      "integrity": "sha512-pb/MYmXstAkysRFx8piNI1tGFNQIFA3vkE3Gq4EuA1dF6gHp/+vgZqsCGJapvy8N3Q+4o7FwvquPJcnZ7RYy4g==",
      "dev": true,
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/import-lazy": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/import-lazy/-/import-lazy-2.1.0.tgz",
      "integrity": "sha1-BWmOPUXIjo1+nZLLBYTnfwlvPkM=",
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/imurmurhash": {
      "version": "0.1.4",
      "resolved": "https://registry.npmjs.org/imurmurhash/-/imurmurhash-0.1.4.tgz",
      "integrity": "sha1-khi5srkoojixPcT7a21XbyMUU+o=",
      "engines": {
        "node": ">=0.8.19"
      }
    },
    "node_modules/indent-string": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/indent-string/-/indent-string-4.0.0.tgz",
      "integrity": "sha512-EdDDZu4A2OyIK7Lr/2zG+w5jmbuk1DVBnEwREQvBzspBJkCEbRa8GxU1lghYcaGJCnRWibjDXlq779X1/y5xwg==",
      "dev": true,
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/infer-owner": {
      "version": "1.0.4",
      "resolved": "https://registry.npmjs.org/infer-owner/-/infer-owner-1.0.4.tgz",
      "integrity": "sha512-IClj+Xz94+d7irH5qRyfJonOdfTzuDaifE6ZPWfx0N0+/ATZCbuTPq2prFl526urkQd90WyUKIh1DfBQ2hMz9A==",
      "dev": true
    },
    "node_modules/inflight": {
      "version": "1.0.6",
      "resolved": "https://registry.npmjs.org/inflight/-/inflight-1.0.6.tgz",
      "integrity": "sha1-Sb1jMdfQLQwJvJEKEHW6gWW1bfk=",
      "dev": true,
      "dependencies": {
        "once": "^1.3.0",
        "wrappy": "1"
      }
    },
    "node_modules/inherits": {
      "version": "2.0.4",
      "resolved": "https://registry.npmjs.org/inherits/-/inherits-2.0.4.tgz",
      "integrity": "sha512-k/vGaX4/Yla3WzyMCvTQOXYeIHvqOKtnqBduzTHpzpQZzAskKMhZ2K+EnBiSM9zGSoIFeMpXKxa4dYeZIQqewQ=="
    },
    "node_modules/ini": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/ini/-/ini-2.0.0.tgz",
      "integrity": "sha512-7PnF4oN3CvZF23ADhA5wRaYEQpJ8qygSkbtTXWBeXWXmEVRXK+1ITciHWwHhsjv1TmW0MgacIv6hEi5pX5NQdA==",
      "engines": {
        "node": ">=10"
      }
    },
    "node_modules/inquirer": {
      "version": "8.2.0",
      "resolved": "https://registry.npmjs.org/inquirer/-/inquirer-8.2.0.tgz",
      "integrity": "sha512-0crLweprevJ02tTuA6ThpoAERAGyVILC4sS74uib58Xf/zSr1/ZWtmm7D5CI+bSQEaA04f0K7idaHpQbSWgiVQ==",
      "dev": true,
      "dependencies": {
        "ansi-escapes": "^4.2.1",
        "chalk": "^4.1.1",
        "cli-cursor": "^3.1.0",
        "cli-width": "^3.0.0",
        "external-editor": "^3.0.3",
        "figures": "^3.0.0",
        "lodash": "^4.17.21",
        "mute-stream": "0.0.8",
        "ora": "^5.4.1",
        "run-async": "^2.4.0",
        "rxjs": "^7.2.0",
        "string-width": "^4.1.0",
        "strip-ansi": "^6.0.0",
        "through": "^2.3.6"
      },
      "engines": {
        "node": ">=8.0.0"
      }
    },
    "node_modules/inquirer/node_modules/ansi-styles": {
      "version": "4.3.0",
      "resolved": "https://registry.npmjs.org/ansi-styles/-/ansi-styles-4.3.0.tgz",
      "integrity": "sha512-zbB9rCJAT1rbjiVDb2hqKFHNYLxgtk8NURxZ3IZwD3F6NtxbXZQCnnSi1Lkx+IDohdPlFp222wVALIheZJQSEg==",
      "dev": true,
      "dependencies": {
        "color-convert": "^2.0.1"
      },
      "engines": {
        "node": ">=8"
      },
      "funding": {
        "url": "https://github.com/chalk/ansi-styles?sponsor=1"
      }
    },
    "node_modules/inquirer/node_modules/chalk": {
      "version": "4.1.2",
      "resolved": "https://registry.npmjs.org/chalk/-/chalk-4.1.2.tgz",
      "integrity": "sha512-oKnbhFyRIXpUuez8iBMmyEa4nbj4IOQyuhc/wy9kY7/WVPcwIO9VA668Pu8RkO7+0G76SLROeyw9CpQ061i4mA==",
      "dev": true,
      "dependencies": {
        "ansi-styles": "^4.1.0",
        "supports-color": "^7.1.0"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/chalk/chalk?sponsor=1"
      }
    },
    "node_modules/inquirer/node_modules/color-convert": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/color-convert/-/color-convert-2.0.1.tgz",
      "integrity": "sha512-RRECPsj7iu/xb5oKYcsFHSppFNnsj/52OVTRKb4zP5onXwVF3zVmmToNcOfGC+CRDpfK/U584fMg38ZHCaElKQ==",
      "dev": true,
      "dependencies": {
        "color-name": "~1.1.4"
      },
      "engines": {
        "node": ">=7.0.0"
      }
    },
    "node_modules/inquirer/node_modules/color-name": {
      "version": "1.1.4",
      "resolved": "https://registry.npmjs.org/color-name/-/color-name-1.1.4.tgz",
      "integrity": "sha512-dOy+3AuW3a2wNbZHIuMZpTcgjGuLU/uBL/ubcZF9OXbDo8ff4O8yVp5Bf0efS8uEoYo5q4Fx7dY9OgQGXgAsQA==",
      "dev": true
    },
    "node_modules/inquirer/node_modules/has-flag": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/has-flag/-/has-flag-4.0.0.tgz",
      "integrity": "sha512-EykJT/Q1KjTWctppgIAgfSO0tKVuZUjhgMr17kqTumMl6Afv3EISleU7qZUzoXDFTAHTDC4NOoG/ZxU3EvlMPQ==",
      "dev": true,
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/inquirer/node_modules/supports-color": {
      "version": "7.2.0",
      "resolved": "https://registry.npmjs.org/supports-color/-/supports-color-7.2.0.tgz",
      "integrity": "sha512-qpCAvRl9stuOHveKsn7HncJRvv501qIacKzQlO/+Lwxc9+0q2wLyv4Dfvt80/DPn2pqOBsJdDiogXGR9+OvwRw==",
      "dev": true,
      "dependencies": {
        "has-flag": "^4.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/ip": {
      "version": "1.1.5",
      "resolved": "https://registry.npmjs.org/ip/-/ip-1.1.5.tgz",
      "integrity": "sha1-vd7XARQpCCjAoDnnLvJfWq7ENUo=",
      "dev": true
    },
    "node_modules/ipaddr.js": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/ipaddr.js/-/ipaddr.js-2.0.1.tgz",
      "integrity": "sha512-1qTgH9NG+IIJ4yfKs2e6Pp1bZg8wbDbKHT21HrLIeYBTRLgMYKnMTPAuI3Lcs61nfx5h1xlXnbJtH1kX5/d/ng==",
      "dev": true,
      "engines": {
        "node": ">= 10"
      }
    },
    "node_modules/is-arguments": {
      "version": "1.1.1",
      "resolved": "https://registry.npmjs.org/is-arguments/-/is-arguments-1.1.1.tgz",
      "integrity": "sha512-8Q7EARjzEnKpt/PCD7e1cgUS0a6X8u5tdSiMqXhojOdoV9TsMsiO+9VLC5vAmO8N7/GmXn7yjR8qnA6bVAEzfA==",
      "dev": true,
      "dependencies": {
        "call-bind": "^1.0.2",
        "has-tostringtag": "^1.0.0"
      },
      "engines": {
        "node": ">= 0.4"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/is-arrayish": {
      "version": "0.2.1",
      "resolved": "https://registry.npmjs.org/is-arrayish/-/is-arrayish-0.2.1.tgz",
      "integrity": "sha1-d8mYQFJ6qOyxqLppe4BkWnqSap0=",
      "dev": true
    },
    "node_modules/is-binary-path": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/is-binary-path/-/is-binary-path-2.1.0.tgz",
      "integrity": "sha512-ZMERYes6pDydyuGidse7OsHxtbI7WVeUEozgR/g7rd0xUimYNlvZRE/K2MgZTjWy725IfelLeVcEM97mmtRGXw==",
      "dev": true,
      "dependencies": {
        "binary-extensions": "^2.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/is-ci": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/is-ci/-/is-ci-2.0.0.tgz",
      "integrity": "sha512-YfJT7rkpQB0updsdHLGWrvhBJfcfzNNawYDNIyQXJz0IViGf75O8EBPKSdvw2rF+LGCsX4FZ8tcr3b19LcZq4w==",
      "dependencies": {
        "ci-info": "^2.0.0"
      },
      "bin": {
        "is-ci": "bin.js"
      }
    },
    "node_modules/is-core-module": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/is-core-module/-/is-core-module-2.8.1.tgz",
      "integrity": "sha512-SdNCUs284hr40hFTFP6l0IfZ/RSrMXF3qgoRHd3/79unUTvrFO/JoXwkGm+5J/Oe3E/b5GsnG330uUNgRpu1PA==",
      "dev": true,
      "dependencies": {
        "has": "^1.0.3"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/is-date-object": {
      "version": "1.0.5",
      "resolved": "https://registry.npmjs.org/is-date-object/-/is-date-object-1.0.5.tgz",
      "integrity": "sha512-9YQaSxsAiSwcvS33MBk3wTCVnWK+HhF8VZR2jRxehM16QcVOdHqPn4VPHmRK4lSr38n9JriurInLcP90xsYNfQ==",
      "dev": true,
      "dependencies": {
        "has-tostringtag": "^1.0.0"
      },
      "engines": {
        "node": ">= 0.4"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/is-docker": {
      "version": "2.2.1",
      "resolved": "https://registry.npmjs.org/is-docker/-/is-docker-2.2.1.tgz",
      "integrity": "sha512-F+i2BKsFrH66iaUFc0woD8sLy8getkwTwtOBjvs56Cx4CgJDeKQeqfz8wAYiSb8JOprWhHH5p77PbmYCvvUuXQ==",
      "dev": true,
      "bin": {
        "is-docker": "cli.js"
      },
      "engines": {
        "node": ">=8"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/is-extglob": {
      "version": "2.1.1",
      "resolved": "https://registry.npmjs.org/is-extglob/-/is-extglob-2.1.1.tgz",
      "integrity": "sha1-qIwCU1eR8C7TfHahueqXc8gz+MI=",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/is-fullwidth-code-point": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/is-fullwidth-code-point/-/is-fullwidth-code-point-3.0.0.tgz",
      "integrity": "sha512-zymm5+u+sCsSWyD9qNaejV3DFvhCKclKdizYaJUuHA83RLjb7nSuGnddCHGv0hk+KY7BMAlsWeK4Ueg6EV6XQg==",
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/is-glob": {
      "version": "4.0.3",
      "resolved": "https://registry.npmjs.org/is-glob/-/is-glob-4.0.3.tgz",
      "integrity": "sha512-xelSayHH36ZgE7ZWhli7pW34hNbNl8Ojv5KVmkJD4hBdD3th8Tfk9vYasLM+mXWOZhFkgZfxhLSnrwRr4elSSg==",
      "dev": true,
      "dependencies": {
        "is-extglob": "^2.1.1"
      },
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/is-installed-globally": {
      "version": "0.4.0",
      "resolved": "https://registry.npmjs.org/is-installed-globally/-/is-installed-globally-0.4.0.tgz",
      "integrity": "sha512-iwGqO3J21aaSkC7jWnHP/difazwS7SFeIqxv6wEtLU8Y5KlzFTjyqcSIT0d8s4+dDhKytsk9PJZ2BkS5eZwQRQ==",
      "dependencies": {
        "global-dirs": "^3.0.0",
        "is-path-inside": "^3.0.2"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/is-interactive": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/is-interactive/-/is-interactive-1.0.0.tgz",
      "integrity": "sha512-2HvIEKRoqS62guEC+qBjpvRubdX910WCMuJTZ+I9yvqKU2/12eSL549HMwtabb4oupdj2sMP50k+XJfB/8JE6w==",
      "dev": true,
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/is-lambda": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/is-lambda/-/is-lambda-1.0.1.tgz",
      "integrity": "sha1-PZh3iZ5qU+/AFgUEzeFfgubwYdU=",
      "dev": true
    },
    "node_modules/is-npm": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/is-npm/-/is-npm-5.0.0.tgz",
      "integrity": "sha512-WW/rQLOazUq+ST/bCAVBp/2oMERWLsR7OrKyt052dNDk4DHcDE0/7QSXITlmi+VBcV13DfIbysG3tZJm5RfdBA==",
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/is-number": {
      "version": "7.0.0",
      "resolved": "https://registry.npmjs.org/is-number/-/is-number-7.0.0.tgz",
      "integrity": "sha512-41Cifkg6e8TylSpdtTpeLVMqvSBEVzTttHvERD741+pnZ8ANv0004MRL43QKPDlK9cGvNp6NZWZUBlbGXYxxng==",
      "dev": true,
      "engines": {
        "node": ">=0.12.0"
      }
    },
    "node_modules/is-obj": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/is-obj/-/is-obj-2.0.0.tgz",
      "integrity": "sha512-drqDG3cbczxxEJRoOXcOjtdp1J/lyp1mNn0xaznRs8+muBhgQcrnbspox5X5fOw0HnMnbfDzvnEMEtqDEJEo8w==",
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/is-path-cwd": {
      "version": "2.2.0",
      "resolved": "https://registry.npmjs.org/is-path-cwd/-/is-path-cwd-2.2.0.tgz",
      "integrity": "sha512-w942bTcih8fdJPJmQHFzkS76NEP8Kzzvmw92cXsazb8intwLqPibPPdXf4ANdKV3rYMuuQYGIWtvz9JilB3NFQ==",
      "dev": true,
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/is-path-inside": {
      "version": "3.0.3",
      "resolved": "https://registry.npmjs.org/is-path-inside/-/is-path-inside-3.0.3.tgz",
      "integrity": "sha512-Fd4gABb+ycGAmKou8eMftCupSir5lRxqf4aD/vd0cD2qc4HL07OjCeuHMr8Ro4CoMaeCKDB0/ECBOVWjTwUvPQ==",
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/is-plain-obj": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/is-plain-obj/-/is-plain-obj-3.0.0.tgz",
      "integrity": "sha512-gwsOE28k+23GP1B6vFl1oVh/WOzmawBrKwo5Ev6wMKzPkaXaCDIQKzLnvsA42DRlbVTWorkgTKIviAKCWkfUwA==",
      "dev": true,
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/is-plain-object": {
      "version": "2.0.4",
      "resolved": "https://registry.npmjs.org/is-plain-object/-/is-plain-object-2.0.4.tgz",
      "integrity": "sha512-h5PpgXkWitc38BBMYawTYMWJHFZJVnBquFE57xFpjB8pJFiF6gZ+bU+WyI/yqXiFR5mdLsgYNaPe8uao6Uv9Og==",
      "dev": true,
      "dependencies": {
        "isobject": "^3.0.1"
      },
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/is-promise": {
      "version": "2.2.2",
      "resolved": "https://registry.npmjs.org/is-promise/-/is-promise-2.2.2.tgz",
      "integrity": "sha512-+lP4/6lKUBfQjZ2pdxThZvLUAafmZb8OAxFb8XXtiQmS35INgr85hdOGoEs124ez1FCnZJt6jau/T+alh58QFQ=="
    },
    "node_modules/is-regex": {
      "version": "1.1.4",
      "resolved": "https://registry.npmjs.org/is-regex/-/is-regex-1.1.4.tgz",
      "integrity": "sha512-kvRdxDsxZjhzUX07ZnLydzS1TU/TJlTUHHY4YLL87e37oUA49DfkLqgy+VjFocowy29cKvcSiu+kIv728jTTVg==",
      "dev": true,
      "dependencies": {
        "call-bind": "^1.0.2",
        "has-tostringtag": "^1.0.0"
      },
      "engines": {
        "node": ">= 0.4"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/is-stream": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/is-stream/-/is-stream-2.0.1.tgz",
      "integrity": "sha512-hFoiJiTl63nn+kstHGBtewWSKnQLpyb155KHheA1l39uvtO9nWIop1p3udqPcUd/xbF1VLMO4n7OI6p7RbngDg==",
      "dev": true,
      "engines": {
        "node": ">=8"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/is-typedarray": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/is-typedarray/-/is-typedarray-1.0.0.tgz",
      "integrity": "sha1-5HnICFjfDBsR3dppQPlgEfzaSpo="
    },
    "node_modules/is-unicode-supported": {
      "version": "0.1.0",
      "resolved": "https://registry.npmjs.org/is-unicode-supported/-/is-unicode-supported-0.1.0.tgz",
      "integrity": "sha512-knxG2q4UC3u8stRGyAVJCOdxFmv5DZiRcdlIaAQXAbSfJya+OhopNotLQrstBhququ4ZpuKbDc/8S6mgXgPFPw==",
      "dev": true,
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/is-what": {
      "version": "3.14.1",
      "resolved": "https://registry.npmjs.org/is-what/-/is-what-3.14.1.tgz",
      "integrity": "sha512-sNxgpk9793nzSs7bA6JQJGeIuRBQhAaNGG77kzYQgMkrID+lS6SlK07K5LaptscDlSaIgH+GPFzf+d75FVxozA==",
      "dev": true
    },
    "node_modules/is-wsl": {
      "version": "2.2.0",
      "resolved": "https://registry.npmjs.org/is-wsl/-/is-wsl-2.2.0.tgz",
      "integrity": "sha512-fKzAra0rGJUUBwGBgNkHZuToZcn+TtXHpeCgmkMJMMYx1sQDYaCSyjJBSCa2nH1DGm7s3n1oBnohoVTBaN7Lww==",
      "dev": true,
      "dependencies": {
        "is-docker": "^2.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/is-yarn-global": {
      "version": "0.3.0",
      "resolved": "https://registry.npmjs.org/is-yarn-global/-/is-yarn-global-0.3.0.tgz",
      "integrity": "sha512-VjSeb/lHmkoyd8ryPVIKvOCn4D1koMqY+vqyjjUfc3xyKtP4dYOxM44sZrnqQSzSds3xyOrUTLTC9LVCVgLngw=="
    },
    "node_modules/isarray": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/isarray/-/isarray-1.0.0.tgz",
      "integrity": "sha1-u5NdSFgsuhaMBoNJV6VKPgcSTxE=",
      "dev": true
    },
    "node_modules/isbinaryfile": {
      "version": "4.0.8",
      "resolved": "https://registry.npmjs.org/isbinaryfile/-/isbinaryfile-4.0.8.tgz",
      "integrity": "sha512-53h6XFniq77YdW+spoRrebh0mnmTxRPTlcuIArO57lmMdq4uBKFKaeTjnb92oYWrSn/LVL+LT+Hap2tFQj8V+w==",
      "dev": true,
      "engines": {
        "node": ">= 8.0.0"
      },
      "funding": {
        "url": "https://github.com/sponsors/gjtorikian/"
      }
    },
    "node_modules/isexe": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/isexe/-/isexe-2.0.0.tgz",
      "integrity": "sha1-6PvzdNxVb/iUehDcsFctYz8s+hA=",
      "dev": true
    },
    "node_modules/isobject": {
      "version": "3.0.1",
      "resolved": "https://registry.npmjs.org/isobject/-/isobject-3.0.1.tgz",
      "integrity": "sha1-TkMekrEalzFjaqH5yNHMvP2reN8=",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/istanbul-lib-coverage": {
      "version": "3.2.0",
      "resolved": "https://registry.npmjs.org/istanbul-lib-coverage/-/istanbul-lib-coverage-3.2.0.tgz",
      "integrity": "sha512-eOeJ5BHCmHYvQK7xt9GkdHuzuCGS1Y6g9Gvnx3Ym33fz/HpLRYxiS0wHNr+m/MBC8B647Xt608vCDEvhl9c6Mw==",
      "dev": true,
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/istanbul-lib-instrument": {
      "version": "5.1.0",
      "resolved": "https://registry.npmjs.org/istanbul-lib-instrument/-/istanbul-lib-instrument-5.1.0.tgz",
      "integrity": "sha512-czwUz525rkOFDJxfKK6mYfIs9zBKILyrZQxjz3ABhjQXhbhFsSbo1HW/BFcsDnfJYJWA6thRR5/TUY2qs5W99Q==",
      "dev": true,
      "dependencies": {
        "@babel/core": "^7.12.3",
        "@babel/parser": "^7.14.7",
        "@istanbuljs/schema": "^0.1.2",
        "istanbul-lib-coverage": "^3.2.0",
        "semver": "^6.3.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/istanbul-lib-instrument/node_modules/semver": {
      "version": "6.3.0",
      "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.0.tgz",
      "integrity": "sha512-b39TBaTSfV6yBrapU89p5fKekE2m/NwnDocOVruQFS1/veMgdzuPcnOM34M6CwxW8jH/lxEa5rBoDeUwu5HHTw==",
      "dev": true,
      "bin": {
        "semver": "bin/semver.js"
      }
    },
    "node_modules/istanbul-lib-report": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/istanbul-lib-report/-/istanbul-lib-report-3.0.0.tgz",
      "integrity": "sha512-wcdi+uAKzfiGT2abPpKZ0hSU1rGQjUQnLvtY5MpQ7QCTahD3VODhcu4wcfY1YtkGaDD5yuydOLINXsfbus9ROw==",
      "dev": true,
      "dependencies": {
        "istanbul-lib-coverage": "^3.0.0",
        "make-dir": "^3.0.0",
        "supports-color": "^7.1.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/istanbul-lib-report/node_modules/has-flag": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/has-flag/-/has-flag-4.0.0.tgz",
      "integrity": "sha512-EykJT/Q1KjTWctppgIAgfSO0tKVuZUjhgMr17kqTumMl6Afv3EISleU7qZUzoXDFTAHTDC4NOoG/ZxU3EvlMPQ==",
      "dev": true,
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/istanbul-lib-report/node_modules/supports-color": {
      "version": "7.2.0",
      "resolved": "https://registry.npmjs.org/supports-color/-/supports-color-7.2.0.tgz",
      "integrity": "sha512-qpCAvRl9stuOHveKsn7HncJRvv501qIacKzQlO/+Lwxc9+0q2wLyv4Dfvt80/DPn2pqOBsJdDiogXGR9+OvwRw==",
      "dev": true,
      "dependencies": {
        "has-flag": "^4.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/istanbul-lib-source-maps": {
      "version": "4.0.1",
      "resolved": "https://registry.npmjs.org/istanbul-lib-source-maps/-/istanbul-lib-source-maps-4.0.1.tgz",
      "integrity": "sha512-n3s8EwkdFIJCG3BPKBYvskgXGoy88ARzvegkitk60NxRdwltLOTaH7CUiMRXvwYorl0Q712iEjcWB+fK/MrWVw==",
      "dev": true,
      "dependencies": {
        "debug": "^4.1.1",
        "istanbul-lib-coverage": "^3.0.0",
        "source-map": "^0.6.1"
      },
      "engines": {
        "node": ">=10"
      }
    },
    "node_modules/istanbul-lib-source-maps/node_modules/source-map": {
      "version": "0.6.1",
      "resolved": "https://registry.npmjs.org/source-map/-/source-map-0.6.1.tgz",
      "integrity": "sha512-UjgapumWlbMhkBgzT7Ykc5YXUT46F0iKu8SGXq0bcwP5dz/h0Plj6enJqjz1Zbq2l5WaqYnrVbwWOWMyF3F47g==",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/istanbul-reports": {
      "version": "3.1.3",
      "resolved": "https://registry.npmjs.org/istanbul-reports/-/istanbul-reports-3.1.3.tgz",
      "integrity": "sha512-x9LtDVtfm/t1GFiLl3NffC7hz+I1ragvgX1P/Lg1NlIagifZDKUkuuaAxH/qpwj2IuEfD8G2Bs/UKp+sZ/pKkg==",
      "dev": true,
      "dependencies": {
        "html-escaper": "^2.0.0",
        "istanbul-lib-report": "^3.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/jasmine-core": {
      "version": "3.10.1",
      "resolved": "https://registry.npmjs.org/jasmine-core/-/jasmine-core-3.10.1.tgz",
      "integrity": "sha512-ooZWSDVAdh79Rrj4/nnfklL3NQVra0BcuhcuWoAwwi+znLDoUeH87AFfeX8s+YeYi6xlv5nveRyaA1v7CintfA==",
      "dev": true
    },
    "node_modules/jest-worker": {
      "version": "27.4.6",
      "resolved": "https://registry.npmjs.org/jest-worker/-/jest-worker-27.4.6.tgz",
      "integrity": "sha512-gHWJF/6Xi5CTG5QCvROr6GcmpIqNYpDJyc8A1h/DyXqH1tD6SnRCM0d3U5msV31D2LB/U+E0M+W4oyvKV44oNw==",
      "dev": true,
      "dependencies": {
        "@types/node": "*",
        "merge-stream": "^2.0.0",
        "supports-color": "^8.0.0"
      },
      "engines": {
        "node": ">= 10.13.0"
      }
    },
    "node_modules/jest-worker/node_modules/has-flag": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/has-flag/-/has-flag-4.0.0.tgz",
      "integrity": "sha512-EykJT/Q1KjTWctppgIAgfSO0tKVuZUjhgMr17kqTumMl6Afv3EISleU7qZUzoXDFTAHTDC4NOoG/ZxU3EvlMPQ==",
      "dev": true,
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/jest-worker/node_modules/supports-color": {
      "version": "8.1.1",
      "resolved": "https://registry.npmjs.org/supports-color/-/supports-color-8.1.1.tgz",
      "integrity": "sha512-MpUEN2OodtUzxvKQl72cUF7RQ5EiHsGvSsVG0ia9c5RbWGL2CI4C7EpPS8UTBIplnlzZiNuV56w+FuNxy3ty2Q==",
      "dev": true,
      "dependencies": {
        "has-flag": "^4.0.0"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/chalk/supports-color?sponsor=1"
      }
    },
    "node_modules/jju": {
      "version": "1.4.0",
      "resolved": "https://registry.npmjs.org/jju/-/jju-1.4.0.tgz",
      "integrity": "sha1-o6vicYryQaKykE+EpiWXDzia4yo="
    },
    "node_modules/js-tokens": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/js-tokens/-/js-tokens-4.0.0.tgz",
      "integrity": "sha512-RdJUflcE3cUzKiMqQgsCu06FPu9UdIJO0beYbPhHN4k6apgJtifcoCtT9bcxOpYBtpD2kCM6Sbzg4CausW/PKQ==",
      "dev": true
    },
    "node_modules/js-yaml": {
      "version": "3.14.1",
      "resolved": "https://registry.npmjs.org/js-yaml/-/js-yaml-3.14.1.tgz",
      "integrity": "sha512-okMH7OXXJ7YrN9Ok3/SXrnu4iX9yOk+25nqX4imS2npuvTYDmo/QEZoqwZkYaIDk3jVvBOTOIEgEhaLOynBS9g==",
      "dev": true,
      "dependencies": {
        "argparse": "^1.0.7",
        "esprima": "^4.0.0"
      },
      "bin": {
        "js-yaml": "bin/js-yaml.js"
      }
    },
    "node_modules/jsesc": {
      "version": "2.5.2",
      "resolved": "https://registry.npmjs.org/jsesc/-/jsesc-2.5.2.tgz",
      "integrity": "sha512-OYu7XEzjkCQ3C5Ps3QIZsQfNpqoJyZZA99wd9aWd05NCtC5pWOkShK2mkL6HXQR6/Cy2lbNdPlZBpuQHXE63gA==",
      "dev": true,
      "bin": {
        "jsesc": "bin/jsesc"
      },
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/json-buffer": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/json-buffer/-/json-buffer-3.0.0.tgz",
      "integrity": "sha1-Wx85evx11ne96Lz8Dkfh+aPZqJg="
    },
    "node_modules/json-parse-better-errors": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/json-parse-better-errors/-/json-parse-better-errors-1.0.2.tgz",
      "integrity": "sha512-mrqyZKfX5EhL7hvqcV6WG1yYjnjeuYDzDhhcAAUrq8Po85NBQBJP+ZDUT75qZQ98IkUoBqdkExkukOU7Ts2wrw==",
      "dev": true
    },
    "node_modules/json-parse-even-better-errors": {
      "version": "2.3.1",
      "resolved": "https://registry.npmjs.org/json-parse-even-better-errors/-/json-parse-even-better-errors-2.3.1.tgz",
      "integrity": "sha512-xyFwyhro/JEof6Ghe2iz2NcXoj2sloNsWr/XsERDK/oiPCfaNhl5ONfp+jQdAZRQQ0IJWNzH9zIZF7li91kh2w==",
      "dev": true
    },
    "node_modules/json-parse-helpfulerror": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/json-parse-helpfulerror/-/json-parse-helpfulerror-1.0.3.tgz",
      "integrity": "sha1-E/FM4C7tTpgSl7ZOueO5MuLdE9w=",
      "dependencies": {
        "jju": "^1.1.0"
      }
    },
    "node_modules/json-schema-traverse": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/json-schema-traverse/-/json-schema-traverse-1.0.0.tgz",
      "integrity": "sha512-NM8/P9n3XjXhIZn1lLhkFaACTOURQXjWhV4BA/RnOv8xvgqtqpAX9IO4mRQxSx1Rlo4tqzeqb0sOlruaOy3dug==",
      "dev": true
    },
    "node_modules/json-server": {
      "version": "0.17.0",
      "resolved": "https://registry.npmjs.org/json-server/-/json-server-0.17.0.tgz",
      "integrity": "sha512-+e/nW0mf666j1yTK+5dRx7hgxq5wJTkc5QhTYa/cBfD6vLlQWHfB4l8XKPgzeO55A8Hqm38g44OtZ5SooXi6MQ==",
      "dependencies": {
        "body-parser": "^1.19.0",
        "chalk": "^4.1.2",
        "compression": "^1.7.4",
        "connect-pause": "^0.1.1",
        "cors": "^2.8.5",
        "errorhandler": "^1.5.1",
        "express": "^4.17.1",
        "express-urlrewrite": "^1.4.0",
        "json-parse-helpfulerror": "^1.0.3",
        "lodash": "^4.17.21",
        "lodash-id": "^0.14.1",
        "lowdb": "^1.0.0",
        "method-override": "^3.0.0",
        "morgan": "^1.10.0",
        "nanoid": "^3.1.23",
        "please-upgrade-node": "^3.2.0",
        "pluralize": "^8.0.0",
        "server-destroy": "^1.0.1",
        "update-notifier": "^5.1.0",
        "yargs": "^17.0.1"
      },
      "bin": {
        "json-server": "lib/cli/bin.js"
      },
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/json-server/node_modules/ansi-styles": {
      "version": "4.3.0",
      "resolved": "https://registry.npmjs.org/ansi-styles/-/ansi-styles-4.3.0.tgz",
      "integrity": "sha512-zbB9rCJAT1rbjiVDb2hqKFHNYLxgtk8NURxZ3IZwD3F6NtxbXZQCnnSi1Lkx+IDohdPlFp222wVALIheZJQSEg==",
      "dependencies": {
        "color-convert": "^2.0.1"
      },
      "engines": {
        "node": ">=8"
      },
      "funding": {
        "url": "https://github.com/chalk/ansi-styles?sponsor=1"
      }
    },
    "node_modules/json-server/node_modules/chalk": {
      "version": "4.1.2",
      "resolved": "https://registry.npmjs.org/chalk/-/chalk-4.1.2.tgz",
      "integrity": "sha512-oKnbhFyRIXpUuez8iBMmyEa4nbj4IOQyuhc/wy9kY7/WVPcwIO9VA668Pu8RkO7+0G76SLROeyw9CpQ061i4mA==",
      "dependencies": {
        "ansi-styles": "^4.1.0",
        "supports-color": "^7.1.0"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/chalk/chalk?sponsor=1"
      }
    },
    "node_modules/json-server/node_modules/color-convert": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/color-convert/-/color-convert-2.0.1.tgz",
      "integrity": "sha512-RRECPsj7iu/xb5oKYcsFHSppFNnsj/52OVTRKb4zP5onXwVF3zVmmToNcOfGC+CRDpfK/U584fMg38ZHCaElKQ==",
      "dependencies": {
        "color-name": "~1.1.4"
      },
      "engines": {
        "node": ">=7.0.0"
      }
    },
    "node_modules/json-server/node_modules/color-name": {
      "version": "1.1.4",
      "resolved": "https://registry.npmjs.org/color-name/-/color-name-1.1.4.tgz",
      "integrity": "sha512-dOy+3AuW3a2wNbZHIuMZpTcgjGuLU/uBL/ubcZF9OXbDo8ff4O8yVp5Bf0efS8uEoYo5q4Fx7dY9OgQGXgAsQA=="
    },
    "node_modules/json-server/node_modules/has-flag": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/has-flag/-/has-flag-4.0.0.tgz",
      "integrity": "sha512-EykJT/Q1KjTWctppgIAgfSO0tKVuZUjhgMr17kqTumMl6Afv3EISleU7qZUzoXDFTAHTDC4NOoG/ZxU3EvlMPQ==",
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/json-server/node_modules/supports-color": {
      "version": "7.2.0",
      "resolved": "https://registry.npmjs.org/supports-color/-/supports-color-7.2.0.tgz",
      "integrity": "sha512-qpCAvRl9stuOHveKsn7HncJRvv501qIacKzQlO/+Lwxc9+0q2wLyv4Dfvt80/DPn2pqOBsJdDiogXGR9+OvwRw==",
      "dependencies": {
        "has-flag": "^4.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/json5": {
      "version": "2.2.0",
      "resolved": "https://registry.npmjs.org/json5/-/json5-2.2.0.tgz",
      "integrity": "sha512-f+8cldu7X/y7RAJurMEJmdoKXGB/X550w2Nr3tTbezL6RwEE/iMcm+tZnXeoZtKuOq6ft8+CqzEkrIgx1fPoQA==",
      "dev": true,
      "dependencies": {
        "minimist": "^1.2.5"
      },
      "bin": {
        "json5": "lib/cli.js"
      },
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/jsonc-parser": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/jsonc-parser/-/jsonc-parser-3.0.0.tgz",
      "integrity": "sha512-fQzRfAbIBnR0IQvftw9FJveWiHp72Fg20giDrHz6TdfB12UH/uue0D3hm57UB5KgAVuniLMCaS8P1IMj9NR7cA==",
      "dev": true
    },
    "node_modules/jsonfile": {
      "version": "6.1.0",
      "resolved": "https://registry.npmjs.org/jsonfile/-/jsonfile-6.1.0.tgz",
      "integrity": "sha512-5dgndWOriYSm5cnYaJNhalLNDKOqFwyDB/rr1E9ZsGciGvKPs8R2xYGCacuf3z6K1YKDz182fd+fY3cn3pMqXQ==",
      "dev": true,
      "dependencies": {
        "universalify": "^2.0.0"
      },
      "optionalDependencies": {
        "graceful-fs": "^4.1.6"
      }
    },
    "node_modules/jsonparse": {
      "version": "1.3.1",
      "resolved": "https://registry.npmjs.org/jsonparse/-/jsonparse-1.3.1.tgz",
      "integrity": "sha1-P02uSpH6wxX3EGL4UhzCOfE2YoA=",
      "dev": true,
      "engines": [
        "node >= 0.2.0"
      ]
    },
    "node_modules/karma": {
      "version": "6.3.12",
      "resolved": "https://registry.npmjs.org/karma/-/karma-6.3.12.tgz",
      "integrity": "sha512-qwIG+oB2YmHx4hjvYSRMNzL3YWAJ9baHaLAxiP7biFNkfpwYTUTtPck0joFpucalNLzMr+7z/FX1uY/kl8DV9A==",
      "dev": true,
      "dependencies": {
        "body-parser": "^1.19.0",
        "braces": "^3.0.2",
        "chokidar": "^3.5.1",
        "colors": "1.4.0",
        "connect": "^3.7.0",
        "di": "^0.0.1",
        "dom-serialize": "^2.2.1",
        "glob": "^7.1.7",
        "graceful-fs": "^4.2.6",
        "http-proxy": "^1.18.1",
        "isbinaryfile": "^4.0.8",
        "lodash": "^4.17.21",
        "log4js": "^6.3.0",
        "mime": "^2.5.2",
        "minimatch": "^3.0.4",
        "qjobs": "^1.2.0",
        "range-parser": "^1.2.1",
        "rimraf": "^3.0.2",
        "socket.io": "^4.2.0",
        "source-map": "^0.6.1",
        "tmp": "^0.2.1",
        "ua-parser-js": "^0.7.30",
        "yargs": "^16.1.1"
      },
      "bin": {
        "karma": "bin/karma"
      },
      "engines": {
        "node": ">= 10"
      }
    },
    "node_modules/karma-chrome-launcher": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/karma-chrome-launcher/-/karma-chrome-launcher-3.1.0.tgz",
      "integrity": "sha512-3dPs/n7vgz1rxxtynpzZTvb9y/GIaW8xjAwcIGttLbycqoFtI7yo1NGnQi6oFTherRE+GIhCAHZC4vEqWGhNvg==",
      "dev": true,
      "dependencies": {
        "which": "^1.2.1"
      }
    },
    "node_modules/karma-coverage": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/karma-coverage/-/karma-coverage-2.1.0.tgz",
      "integrity": "sha512-uIejpnArNFQIovB6EPsKO/T4XofELdJWXcA2ADXztFlKhHbr0Ws6ba7wKTMVWsIhEs4iJxdhQkCQrkkhFJSZCw==",
      "dev": true,
      "dependencies": {
        "istanbul-lib-coverage": "^3.2.0",
        "istanbul-lib-instrument": "^4.0.3",
        "istanbul-lib-report": "^3.0.0",
        "istanbul-lib-source-maps": "^4.0.1",
        "istanbul-reports": "^3.0.5",
        "minimatch": "^3.0.4"
      },
      "engines": {
        "node": ">=10.0.0"
      }
    },
    "node_modules/karma-coverage/node_modules/istanbul-lib-instrument": {
      "version": "4.0.3",
      "resolved": "https://registry.npmjs.org/istanbul-lib-instrument/-/istanbul-lib-instrument-4.0.3.tgz",
      "integrity": "sha512-BXgQl9kf4WTCPCCpmFGoJkz/+uhvm7h7PFKUYxh7qarQd3ER33vHG//qaE8eN25l07YqZPpHXU9I09l/RD5aGQ==",
      "dev": true,
      "dependencies": {
        "@babel/core": "^7.7.5",
        "@istanbuljs/schema": "^0.1.2",
        "istanbul-lib-coverage": "^3.0.0",
        "semver": "^6.3.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/karma-coverage/node_modules/semver": {
      "version": "6.3.0",
      "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.0.tgz",
      "integrity": "sha512-b39TBaTSfV6yBrapU89p5fKekE2m/NwnDocOVruQFS1/veMgdzuPcnOM34M6CwxW8jH/lxEa5rBoDeUwu5HHTw==",
      "dev": true,
      "bin": {
        "semver": "bin/semver.js"
      }
    },
    "node_modules/karma-jasmine": {
      "version": "4.0.1",
      "resolved": "https://registry.npmjs.org/karma-jasmine/-/karma-jasmine-4.0.1.tgz",
      "integrity": "sha512-h8XDAhTiZjJKzfkoO1laMH+zfNlra+dEQHUAjpn5JV1zCPtOIVWGQjLBrqhnzQa/hrU2XrZwSyBa6XjEBzfXzw==",
      "dev": true,
      "dependencies": {
        "jasmine-core": "^3.6.0"
      },
      "engines": {
        "node": ">= 10"
      },
      "peerDependencies": {
        "karma": "*"
      }
    },
    "node_modules/karma-jasmine-html-reporter": {
      "version": "1.7.0",
      "resolved": "https://registry.npmjs.org/karma-jasmine-html-reporter/-/karma-jasmine-html-reporter-1.7.0.tgz",
      "integrity": "sha512-pzum1TL7j90DTE86eFt48/s12hqwQuiD+e5aXx2Dc9wDEn2LfGq6RoAxEZZjFiN0RDSCOnosEKRZWxbQ+iMpQQ==",
      "dev": true,
      "peerDependencies": {
        "jasmine-core": ">=3.8",
        "karma": ">=0.9",
        "karma-jasmine": ">=1.1"
      }
    },
    "node_modules/karma-source-map-support": {
      "version": "1.4.0",
      "resolved": "https://registry.npmjs.org/karma-source-map-support/-/karma-source-map-support-1.4.0.tgz",
      "integrity": "sha512-RsBECncGO17KAoJCYXjv+ckIz+Ii9NCi+9enk+rq6XC81ezYkb4/RHE6CTXdA7IOJqoF3wcaLfVG0CPmE5ca6A==",
      "dev": true,
      "dependencies": {
        "source-map-support": "^0.5.5"
      }
    },
    "node_modules/karma/node_modules/source-map": {
      "version": "0.6.1",
      "resolved": "https://registry.npmjs.org/source-map/-/source-map-0.6.1.tgz",
      "integrity": "sha512-UjgapumWlbMhkBgzT7Ykc5YXUT46F0iKu8SGXq0bcwP5dz/h0Plj6enJqjz1Zbq2l5WaqYnrVbwWOWMyF3F47g==",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/karma/node_modules/tmp": {
      "version": "0.2.1",
      "resolved": "https://registry.npmjs.org/tmp/-/tmp-0.2.1.tgz",
      "integrity": "sha512-76SUhtfqR2Ijn+xllcI5P1oyannHNHByD80W1q447gU3mp9G9PSpGdWmjUOHRDPiHYacIk66W7ubDTuPF3BEtQ==",
      "dev": true,
      "dependencies": {
        "rimraf": "^3.0.0"
      },
      "engines": {
        "node": ">=8.17.0"
      }
    },
    "node_modules/karma/node_modules/yargs": {
      "version": "16.2.0",
      "resolved": "https://registry.npmjs.org/yargs/-/yargs-16.2.0.tgz",
      "integrity": "sha512-D1mvvtDG0L5ft/jGWkLpG1+m0eQxOfaBvTNELraWj22wSVUMWxZUvYgJYcKh6jGGIkJFhH4IZPQhR4TKpc8mBw==",
      "dev": true,
      "dependencies": {
        "cliui": "^7.0.2",
        "escalade": "^3.1.1",
        "get-caller-file": "^2.0.5",
        "require-directory": "^2.1.1",
        "string-width": "^4.2.0",
        "y18n": "^5.0.5",
        "yargs-parser": "^20.2.2"
      },
      "engines": {
        "node": ">=10"
      }
    },
    "node_modules/karma/node_modules/yargs-parser": {
      "version": "20.2.9",
      "resolved": "https://registry.npmjs.org/yargs-parser/-/yargs-parser-20.2.9.tgz",
      "integrity": "sha512-y11nGElTIV+CT3Zv9t7VKl+Q3hTQoT9a1Qzezhhl6Rp21gJ/IVTW7Z3y9EWXhuUBC2Shnf+DX0antecpAwSP8w==",
      "dev": true,
      "engines": {
        "node": ">=10"
      }
    },
    "node_modules/keyv": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/keyv/-/keyv-3.1.0.tgz",
      "integrity": "sha512-9ykJ/46SN/9KPM/sichzQ7OvXyGDYKGTaDlKMGCAlg2UK8KRy4jb0d8sFc+0Tt0YYnThq8X2RZgCg74RPxgcVA==",
      "dependencies": {
        "json-buffer": "3.0.0"
      }
    },
    "node_modules/kind-of": {
      "version": "6.0.3",
      "resolved": "https://registry.npmjs.org/kind-of/-/kind-of-6.0.3.tgz",
      "integrity": "sha512-dcS1ul+9tmeD95T+x28/ehLgd9mENa3LsvDTtzm3vyBEO7RPptvAD+t44WVXaUjTBRcrpFeFlC8WCruUR456hw==",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/klona": {
      "version": "2.0.5",
      "resolved": "https://registry.npmjs.org/klona/-/klona-2.0.5.tgz",
      "integrity": "sha512-pJiBpiXMbt7dkzXe8Ghj/u4FfXOOa98fPW+bihOJ4SjnoijweJrNThJfd3ifXpXhREjpoF2mZVH1GfS9LV3kHQ==",
      "dev": true,
      "engines": {
        "node": ">= 8"
      }
    },
    "node_modules/latest-version": {
      "version": "5.1.0",
      "resolved": "https://registry.npmjs.org/latest-version/-/latest-version-5.1.0.tgz",
      "integrity": "sha512-weT+r0kTkRQdCdYCNtkMwWXQTMEswKrFBkm4ckQOMVhhqhIMI1UT2hMj+1iigIhgSZm5gTmrRXBNoGUgaTY1xA==",
      "dependencies": {
        "package-json": "^6.3.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/less": {
      "version": "4.1.2",
      "resolved": "https://registry.npmjs.org/less/-/less-4.1.2.tgz",
      "integrity": "sha512-EoQp/Et7OSOVu0aJknJOtlXZsnr8XE8KwuzTHOLeVSEx8pVWUICc8Q0VYRHgzyjX78nMEyC/oztWFbgyhtNfDA==",
      "dev": true,
      "dependencies": {
        "copy-anything": "^2.0.1",
        "parse-node-version": "^1.0.1",
        "tslib": "^2.3.0"
      },
      "bin": {
        "lessc": "bin/lessc"
      },
      "engines": {
        "node": ">=6"
      },
      "optionalDependencies": {
        "errno": "^0.1.1",
        "graceful-fs": "^4.1.2",
        "image-size": "~0.5.0",
        "make-dir": "^2.1.0",
        "mime": "^1.4.1",
        "needle": "^2.5.2",
        "source-map": "~0.6.0"
      }
    },
    "node_modules/less-loader": {
      "version": "10.2.0",
      "resolved": "https://registry.npmjs.org/less-loader/-/less-loader-10.2.0.tgz",
      "integrity": "sha512-AV5KHWvCezW27GT90WATaDnfXBv99llDbtaj4bshq6DvAihMdNjaPDcUMa6EXKLRF+P2opFenJp89BXg91XLYg==",
      "dev": true,
      "dependencies": {
        "klona": "^2.0.4"
      },
      "engines": {
        "node": ">= 12.13.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/webpack"
      },
      "peerDependencies": {
        "less": "^3.5.0 || ^4.0.0",
        "webpack": "^5.0.0"
      }
    },
    "node_modules/less/node_modules/make-dir": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/make-dir/-/make-dir-2.1.0.tgz",
      "integrity": "sha512-LS9X+dc8KLxXCb8dni79fLIIUA5VyZoyjSMCwTluaXA0o27cCK0bhXkpgw+sTXVpPy/lSO57ilRixqk0vDmtRA==",
      "dev": true,
      "optional": true,
      "dependencies": {
        "pify": "^4.0.1",
        "semver": "^5.6.0"
      },
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/less/node_modules/mime": {
      "version": "1.6.0",
      "resolved": "https://registry.npmjs.org/mime/-/mime-1.6.0.tgz",
      "integrity": "sha512-x0Vn8spI+wuJ1O6S7gnbaQg8Pxh4NNHb7KSINmEWKiPE4RKOplvijn+NkmYmmRgP68mc70j2EbeTFRsrswaQeg==",
      "dev": true,
      "optional": true,
      "bin": {
        "mime": "cli.js"
      },
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/less/node_modules/pify": {
      "version": "4.0.1",
      "resolved": "https://registry.npmjs.org/pify/-/pify-4.0.1.tgz",
      "integrity": "sha512-uB80kBFb/tfd68bVleG9T5GGsGPjJrLAUpR5PZIrhBnIaRTQRjqdJSsIKkOP6OAIFbj7GOrcudc5pNjZ+geV2g==",
      "dev": true,
      "optional": true,
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/less/node_modules/semver": {
      "version": "5.7.1",
      "resolved": "https://registry.npmjs.org/semver/-/semver-5.7.1.tgz",
      "integrity": "sha512-sauaDf/PZdVgrLTNYHRtpXa1iRiKcaebiKQ1BJdpQlWH2lCvexQdX55snPFyK7QzpudqbCI0qXFfOasHdyNDGQ==",
      "dev": true,
      "optional": true,
      "bin": {
        "semver": "bin/semver"
      }
    },
    "node_modules/less/node_modules/source-map": {
      "version": "0.6.1",
      "resolved": "https://registry.npmjs.org/source-map/-/source-map-0.6.1.tgz",
      "integrity": "sha512-UjgapumWlbMhkBgzT7Ykc5YXUT46F0iKu8SGXq0bcwP5dz/h0Plj6enJqjz1Zbq2l5WaqYnrVbwWOWMyF3F47g==",
      "dev": true,
      "optional": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/license-webpack-plugin": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/license-webpack-plugin/-/license-webpack-plugin-4.0.0.tgz",
      "integrity": "sha512-b9iMrROrw2fTOJBZ57h0xJfT5/1Cxg4ucYbtpWoukv4Awb2TFPfDDFVHNM8w6SYQpVfB13a5tQJxgGamqwrsyw==",
      "dev": true,
      "dependencies": {
        "webpack-sources": "^3.0.0"
      },
      "peerDependenciesMeta": {
        "webpack": {
          "optional": true
        },
        "webpack-sources": {
          "optional": true
        }
      }
    },
    "node_modules/lines-and-columns": {
      "version": "1.2.4",
      "resolved": "https://registry.npmjs.org/lines-and-columns/-/lines-and-columns-1.2.4.tgz",
      "integrity": "sha512-7ylylesZQ/PV29jhEDl3Ufjo6ZX7gCqJr5F7PKrqc93v7fzSymt1BpwEU8nAUXs8qzzvqhbjhK5QZg6Mt/HkBg==",
      "dev": true
    },
    "node_modules/loader-runner": {
      "version": "4.2.0",
      "resolved": "https://registry.npmjs.org/loader-runner/-/loader-runner-4.2.0.tgz",
      "integrity": "sha512-92+huvxMvYlMzMt0iIOukcwYBFpkYJdpl2xsZ7LrlayO7E8SOv+JJUEK17B/dJIHAOLMfh2dZZ/Y18WgmGtYNw==",
      "dev": true,
      "engines": {
        "node": ">=6.11.5"
      }
    },
    "node_modules/loader-utils": {
      "version": "3.2.0",
      "resolved": "https://registry.npmjs.org/loader-utils/-/loader-utils-3.2.0.tgz",
      "integrity": "sha512-HVl9ZqccQihZ7JM85dco1MvO9G+ONvxoGa9rkhzFsneGLKSUg1gJf9bWzhRhcvm2qChhWpebQhP44qxjKIUCaQ==",
      "dev": true,
      "engines": {
        "node": ">= 12.13.0"
      }
    },
    "node_modules/locate-path": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/locate-path/-/locate-path-5.0.0.tgz",
      "integrity": "sha512-t7hw9pI+WvuwNJXwk5zVHpyhIqzg2qTlklJOf0mVxGSbe3Fp2VieZcduNYjaLDoy6p9uGpQEGWG87WpMKlNq8g==",
      "dev": true,
      "dependencies": {
        "p-locate": "^4.1.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/lodash": {
      "version": "4.17.21",
      "resolved": "https://registry.npmjs.org/lodash/-/lodash-4.17.21.tgz",
      "integrity": "sha512-v2kDEe57lecTulaDIuNTPy3Ry4gLGJ6Z1O3vE1krgXZNrsQ+LFTGHVxVjcXPs17LhbZVGedAJv8XZ1tvj5FvSg=="
    },
    "node_modules/lodash-id": {
      "version": "0.14.1",
      "resolved": "https://registry.npmjs.org/lodash-id/-/lodash-id-0.14.1.tgz",
      "integrity": "sha512-ikQPBTiq/d5m6dfKQlFdIXFzvThPi2Be9/AHxktOnDSfSxE1j9ICbBT5Elk1ke7HSTgM38LHTpmJovo9/klnLg==",
      "engines": {
        "node": ">= 4"
      }
    },
    "node_modules/lodash.debounce": {
      "version": "4.0.8",
      "resolved": "https://registry.npmjs.org/lodash.debounce/-/lodash.debounce-4.0.8.tgz",
      "integrity": "sha1-gteb/zCmfEAF/9XiUVMArZyk168=",
      "dev": true
    },
    "node_modules/log-symbols": {
      "version": "4.1.0",
      "resolved": "https://registry.npmjs.org/log-symbols/-/log-symbols-4.1.0.tgz",
      "integrity": "sha512-8XPvpAA8uyhfteu8pIvQxpJZ7SYYdpUivZpGy6sFsBuKRY/7rQGavedeB8aK+Zkyq6upMFVL/9AW6vOYzfRyLg==",
      "dev": true,
      "dependencies": {
        "chalk": "^4.1.0",
        "is-unicode-supported": "^0.1.0"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/log-symbols/node_modules/ansi-styles": {
      "version": "4.3.0",
      "resolved": "https://registry.npmjs.org/ansi-styles/-/ansi-styles-4.3.0.tgz",
      "integrity": "sha512-zbB9rCJAT1rbjiVDb2hqKFHNYLxgtk8NURxZ3IZwD3F6NtxbXZQCnnSi1Lkx+IDohdPlFp222wVALIheZJQSEg==",
      "dev": true,
      "dependencies": {
        "color-convert": "^2.0.1"
      },
      "engines": {
        "node": ">=8"
      },
      "funding": {
        "url": "https://github.com/chalk/ansi-styles?sponsor=1"
      }
    },
    "node_modules/log-symbols/node_modules/chalk": {
      "version": "4.1.2",
      "resolved": "https://registry.npmjs.org/chalk/-/chalk-4.1.2.tgz",
      "integrity": "sha512-oKnbhFyRIXpUuez8iBMmyEa4nbj4IOQyuhc/wy9kY7/WVPcwIO9VA668Pu8RkO7+0G76SLROeyw9CpQ061i4mA==",
      "dev": true,
      "dependencies": {
        "ansi-styles": "^4.1.0",
        "supports-color": "^7.1.0"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/chalk/chalk?sponsor=1"
      }
    },
    "node_modules/log-symbols/node_modules/color-convert": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/color-convert/-/color-convert-2.0.1.tgz",
      "integrity": "sha512-RRECPsj7iu/xb5oKYcsFHSppFNnsj/52OVTRKb4zP5onXwVF3zVmmToNcOfGC+CRDpfK/U584fMg38ZHCaElKQ==",
      "dev": true,
      "dependencies": {
        "color-name": "~1.1.4"
      },
      "engines": {
        "node": ">=7.0.0"
      }
    },
    "node_modules/log-symbols/node_modules/color-name": {
      "version": "1.1.4",
      "resolved": "https://registry.npmjs.org/color-name/-/color-name-1.1.4.tgz",
      "integrity": "sha512-dOy+3AuW3a2wNbZHIuMZpTcgjGuLU/uBL/ubcZF9OXbDo8ff4O8yVp5Bf0efS8uEoYo5q4Fx7dY9OgQGXgAsQA==",
      "dev": true
    },
    "node_modules/log-symbols/node_modules/has-flag": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/has-flag/-/has-flag-4.0.0.tgz",
      "integrity": "sha512-EykJT/Q1KjTWctppgIAgfSO0tKVuZUjhgMr17kqTumMl6Afv3EISleU7qZUzoXDFTAHTDC4NOoG/ZxU3EvlMPQ==",
      "dev": true,
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/log-symbols/node_modules/supports-color": {
      "version": "7.2.0",
      "resolved": "https://registry.npmjs.org/supports-color/-/supports-color-7.2.0.tgz",
      "integrity": "sha512-qpCAvRl9stuOHveKsn7HncJRvv501qIacKzQlO/+Lwxc9+0q2wLyv4Dfvt80/DPn2pqOBsJdDiogXGR9+OvwRw==",
      "dev": true,
      "dependencies": {
        "has-flag": "^4.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/log4js": {
      "version": "6.4.1",
      "resolved": "https://registry.npmjs.org/log4js/-/log4js-6.4.1.tgz",
      "integrity": "sha512-iUiYnXqAmNKiIZ1XSAitQ4TmNs8CdZYTAWINARF3LjnsLN8tY5m0vRwd6uuWj/yNY0YHxeZodnbmxKFUOM2rMg==",
      "dev": true,
      "dependencies": {
        "date-format": "^4.0.3",
        "debug": "^4.3.3",
        "flatted": "^3.2.4",
        "rfdc": "^1.3.0",
        "streamroller": "^3.0.2"
      },
      "engines": {
        "node": ">=8.0"
      }
    },
    "node_modules/lowdb": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/lowdb/-/lowdb-1.0.0.tgz",
      "integrity": "sha512-2+x8esE/Wb9SQ1F9IHaYWfsC9FIecLOPrK4g17FGEayjUWH172H6nwicRovGvSE2CPZouc2MCIqCI7h9d+GftQ==",
      "dependencies": {
        "graceful-fs": "^4.1.3",
        "is-promise": "^2.1.0",
        "lodash": "4",
        "pify": "^3.0.0",
        "steno": "^0.4.1"
      },
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/lowdb/node_modules/pify": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/pify/-/pify-3.0.0.tgz",
      "integrity": "sha1-5aSs0sEB/fPZpNB/DbxNtJ3SgXY=",
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/lowercase-keys": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/lowercase-keys/-/lowercase-keys-1.0.1.tgz",
      "integrity": "sha512-G2Lj61tXDnVFFOi8VZds+SoQjtQC3dgokKdDG2mTm1tx4m50NUHBOZSBwQQHyy0V12A0JTG4icfZQH+xPyh8VA==",
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/lru-cache": {
      "version": "6.0.0",
      "resolved": "https://registry.npmjs.org/lru-cache/-/lru-cache-6.0.0.tgz",
      "integrity": "sha512-Jo6dJ04CmSjuznwJSS3pUeWmd/H0ffTlkXXgwZi+eq1UCmqQwCh+eLsYOYCwY991i2Fah4h1BEMCx4qThGbsiA==",
      "dependencies": {
        "yallist": "^4.0.0"
      },
      "engines": {
        "node": ">=10"
      }
    },
    "node_modules/magic-string": {
      "version": "0.25.7",
      "resolved": "https://registry.npmjs.org/magic-string/-/magic-string-0.25.7.tgz",
      "integrity": "sha512-4CrMT5DOHTDk4HYDlzmwu4FVCcIYI8gauveasrdCu2IKIFOJ3f0v/8MDGJCDL9oD2ppz/Av1b0Nj345H9M+XIA==",
      "dev": true,
      "dependencies": {
        "sourcemap-codec": "^1.4.4"
      }
    },
    "node_modules/make-dir": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/make-dir/-/make-dir-3.1.0.tgz",
      "integrity": "sha512-g3FeP20LNwhALb/6Cz6Dd4F2ngze0jz7tbzrD2wAV+o9FeNHe4rL+yK2md0J/fiSf1sa1ADhXqi5+oVwOM/eGw==",
      "dependencies": {
        "semver": "^6.0.0"
      },
      "engines": {
        "node": ">=8"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/make-dir/node_modules/semver": {
      "version": "6.3.0",
      "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.0.tgz",
      "integrity": "sha512-b39TBaTSfV6yBrapU89p5fKekE2m/NwnDocOVruQFS1/veMgdzuPcnOM34M6CwxW8jH/lxEa5rBoDeUwu5HHTw==",
      "bin": {
        "semver": "bin/semver.js"
      }
    },
    "node_modules/make-fetch-happen": {
      "version": "9.1.0",
      "resolved": "https://registry.npmjs.org/make-fetch-happen/-/make-fetch-happen-9.1.0.tgz",
      "integrity": "sha512-+zopwDy7DNknmwPQplem5lAZX/eCOzSvSNNcSKm5eVwTkOBzoktEfXsa9L23J/GIRhxRsaxzkPEhrJEpE2F4Gg==",
      "dev": true,
      "dependencies": {
        "agentkeepalive": "^4.1.3",
        "cacache": "^15.2.0",
        "http-cache-semantics": "^4.1.0",
        "http-proxy-agent": "^4.0.1",
        "https-proxy-agent": "^5.0.0",
        "is-lambda": "^1.0.1",
        "lru-cache": "^6.0.0",
        "minipass": "^3.1.3",
        "minipass-collect": "^1.0.2",
        "minipass-fetch": "^1.3.2",
        "minipass-flush": "^1.0.5",
        "minipass-pipeline": "^1.2.4",
        "negotiator": "^0.6.2",
        "promise-retry": "^2.0.1",
        "socks-proxy-agent": "^6.0.0",
        "ssri": "^8.0.0"
      },
      "engines": {
        "node": ">= 10"
      }
    },
    "node_modules/media-typer": {
      "version": "0.3.0",
      "resolved": "https://registry.npmjs.org/media-typer/-/media-typer-0.3.0.tgz",
      "integrity": "sha1-hxDXrwqmJvj/+hzgAWhUUmMlV0g=",
      "engines": {
        "node": ">= 0.6"
      }
    },
    "node_modules/memfs": {
      "version": "3.4.1",
      "resolved": "https://registry.npmjs.org/memfs/-/memfs-3.4.1.tgz",
      "integrity": "sha512-1c9VPVvW5P7I85c35zAdEr1TD5+F11IToIHIlrVIcflfnzPkJa0ZoYEoEdYDP8KgPFoSZ/opDrUsAoZWym3mtw==",
      "dev": true,
      "dependencies": {
        "fs-monkey": "1.0.3"
      },
      "engines": {
        "node": ">= 4.0.0"
      }
    },
    "node_modules/merge-descriptors": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/merge-descriptors/-/merge-descriptors-1.0.1.tgz",
      "integrity": "sha1-sAqqVW3YtEVoFQ7J0blT8/kMu2E="
    },
    "node_modules/merge-stream": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/merge-stream/-/merge-stream-2.0.0.tgz",
      "integrity": "sha512-abv/qOcuPfk3URPfDzmZU1LKmuw8kT+0nIHvKrKgFrwifol/doWcdA4ZqsWQ8ENrFKkd67Mfpo/LovbIUsbt3w==",
      "dev": true
    },
    "node_modules/merge2": {
      "version": "1.4.1",
      "resolved": "https://registry.npmjs.org/merge2/-/merge2-1.4.1.tgz",
      "integrity": "sha512-8q7VEgMJW4J8tcfVPy8g09NcQwZdbwFEqhe/WZkoIzjn/3TGDwtOCYtXGxA3O8tPzpczCCDgv+P2P5y00ZJOOg==",
      "dev": true,
      "engines": {
        "node": ">= 8"
      }
    },
    "node_modules/method-override": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/method-override/-/method-override-3.0.0.tgz",
      "integrity": "sha512-IJ2NNN/mSl9w3kzWB92rcdHpz+HjkxhDJWNDBqSlas+zQdP8wBiJzITPg08M/k2uVvMow7Sk41atndNtt/PHSA==",
      "dependencies": {
        "debug": "3.1.0",
        "methods": "~1.1.2",
        "parseurl": "~1.3.2",
        "vary": "~1.1.2"
      },
      "engines": {
        "node": ">= 0.10"
      }
    },
    "node_modules/method-override/node_modules/debug": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/debug/-/debug-3.1.0.tgz",
      "integrity": "sha512-OX8XqP7/1a9cqkxYw2yXss15f26NKWBpDXQd0/uK/KPqdQhxbPa994hnzjcE2VqQpDslf55723cKPUOGSmMY3g==",
      "dependencies": {
        "ms": "2.0.0"
      }
    },
    "node_modules/method-override/node_modules/ms": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/ms/-/ms-2.0.0.tgz",
      "integrity": "sha1-VgiurfwAvmwpAd9fmGF4jeDVl8g="
    },
    "node_modules/methods": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/methods/-/methods-1.1.2.tgz",
      "integrity": "sha1-VSmk1nZUE07cxSZmVoNbD4Ua/O4=",
      "engines": {
        "node": ">= 0.6"
      }
    },
    "node_modules/micromatch": {
      "version": "4.0.4",
      "resolved": "https://registry.npmjs.org/micromatch/-/micromatch-4.0.4.tgz",
      "integrity": "sha512-pRmzw/XUcwXGpD9aI9q/0XOwLNygjETJ8y0ao0wdqprrzDa4YnxLcz7fQRZr8voh8V10kGhABbNcHVk5wHgWwg==",
      "dev": true,
      "dependencies": {
        "braces": "^3.0.1",
        "picomatch": "^2.2.3"
      },
      "engines": {
        "node": ">=8.6"
      }
    },
    "node_modules/mime": {
      "version": "2.6.0",
      "resolved": "https://registry.npmjs.org/mime/-/mime-2.6.0.tgz",
      "integrity": "sha512-USPkMeET31rOMiarsBNIHZKLGgvKc/LrjofAnBlOttf5ajRvqiRA8QsenbcooctK6d6Ts6aqZXBA+XbkKthiQg==",
      "dev": true,
      "bin": {
        "mime": "cli.js"
      },
      "engines": {
        "node": ">=4.0.0"
      }
    },
    "node_modules/mime-db": {
      "version": "1.51.0",
      "resolved": "https://registry.npmjs.org/mime-db/-/mime-db-1.51.0.tgz",
      "integrity": "sha512-5y8A56jg7XVQx2mbv1lu49NR4dokRnhZYTtL+KGfaa27uq4pSTXkwQkFJl4pkRMyNFz/EtYDSkiiEHx3F7UN6g==",
      "engines": {
        "node": ">= 0.6"
      }
    },
    "node_modules/mime-types": {
      "version": "2.1.34",
      "resolved": "https://registry.npmjs.org/mime-types/-/mime-types-2.1.34.tgz",
      "integrity": "sha512-6cP692WwGIs9XXdOO4++N+7qjqv0rqxxVvJ3VHPh/Sc9mVZcQP+ZGhkKiTvWMQRr2tbHkJP/Yn7Y0npb3ZBs4A==",
      "dependencies": {
        "mime-db": "1.51.0"
      },
      "engines": {
        "node": ">= 0.6"
      }
    },
    "node_modules/mimic-fn": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/mimic-fn/-/mimic-fn-2.1.0.tgz",
      "integrity": "sha512-OqbOk5oEQeAZ8WXWydlu9HJjz9WVdEIvamMCcXmuqUYjTknH/sqsWvhQ3vgwKFRR1HpjvNBKQ37nbJgYzGqGcg==",
      "dev": true,
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/mimic-response": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/mimic-response/-/mimic-response-1.0.1.tgz",
      "integrity": "sha512-j5EctnkH7amfV/q5Hgmoal1g2QHFJRraOtmx0JpIqkxhBhI/lJSl1nMpQ45hVarwNETOoWEimndZ4QK0RHxuxQ==",
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/mini-css-extract-plugin": {
      "version": "2.4.5",
      "resolved": "https://registry.npmjs.org/mini-css-extract-plugin/-/mini-css-extract-plugin-2.4.5.tgz",
      "integrity": "sha512-oEIhRucyn1JbT/1tU2BhnwO6ft1jjH1iCX9Gc59WFMg0n5773rQU0oyQ0zzeYFFuBfONaRbQJyGoPtuNseMxjA==",
      "dev": true,
      "dependencies": {
        "schema-utils": "^4.0.0"
      },
      "engines": {
        "node": ">= 12.13.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/webpack"
      },
      "peerDependencies": {
        "webpack": "^5.0.0"
      }
    },
    "node_modules/mini-css-extract-plugin/node_modules/schema-utils": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/schema-utils/-/schema-utils-4.0.0.tgz",
      "integrity": "sha512-1edyXKgh6XnJsJSQ8mKWXnN/BVaIbFMLpouRUrXgVq7WYne5kw3MW7UPhO44uRXQSIpTSXoJbmrR2X0w9kUTyg==",
      "dev": true,
      "dependencies": {
        "@types/json-schema": "^7.0.9",
        "ajv": "^8.8.0",
        "ajv-formats": "^2.1.1",
        "ajv-keywords": "^5.0.0"
      },
      "engines": {
        "node": ">= 12.13.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/webpack"
      }
    },
    "node_modules/minimalistic-assert": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/minimalistic-assert/-/minimalistic-assert-1.0.1.tgz",
      "integrity": "sha512-UtJcAD4yEaGtjPezWuO9wC4nwUnVH/8/Im3yEHQP4b67cXlD/Qr9hdITCU1xDbSEXg2XKNaP8jsReV7vQd00/A==",
      "dev": true
    },
    "node_modules/minimatch": {
      "version": "3.0.4",
      "resolved": "https://registry.npmjs.org/minimatch/-/minimatch-3.0.4.tgz",
      "integrity": "sha512-yJHVQEhyqPLUTgt9B83PXu6W3rx4MvvHvSUvToogpwoGDOUQ+yDrR0HRot+yOCdCO7u4hX3pWft6kWBBcqh0UA==",
      "dev": true,
      "dependencies": {
        "brace-expansion": "^1.1.7"
      },
      "engines": {
        "node": "*"
      }
    },
    "node_modules/minimist": {
      "version": "1.2.5",
      "resolved": "https://registry.npmjs.org/minimist/-/minimist-1.2.5.tgz",
      "integrity": "sha512-FM9nNUYrRBAELZQT3xeZQ7fmMOBg6nWNmJKTcgsJeaLstP/UODVpGsr5OhXhhXg6f+qtJ8uiZ+PUxkDWcgIXLw=="
    },
    "node_modules/minipass": {
      "version": "3.1.6",
      "resolved": "https://registry.npmjs.org/minipass/-/minipass-3.1.6.tgz",
      "integrity": "sha512-rty5kpw9/z8SX9dmxblFA6edItUmwJgMeYDZRrwlIVN27i8gysGbznJwUggw2V/FVqFSDdWy040ZPS811DYAqQ==",
      "dev": true,
      "dependencies": {
        "yallist": "^4.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/minipass-collect": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/minipass-collect/-/minipass-collect-1.0.2.tgz",
      "integrity": "sha512-6T6lH0H8OG9kITm/Jm6tdooIbogG9e0tLgpY6mphXSm/A9u8Nq1ryBG+Qspiub9LjWlBPsPS3tWQ/Botq4FdxA==",
      "dev": true,
      "dependencies": {
        "minipass": "^3.0.0"
      },
      "engines": {
        "node": ">= 8"
      }
    },
    "node_modules/minipass-fetch": {
      "version": "1.4.1",
      "resolved": "https://registry.npmjs.org/minipass-fetch/-/minipass-fetch-1.4.1.tgz",
      "integrity": "sha512-CGH1eblLq26Y15+Azk7ey4xh0J/XfJfrCox5LDJiKqI2Q2iwOLOKrlmIaODiSQS8d18jalF6y2K2ePUm0CmShw==",
      "dev": true,
      "dependencies": {
        "minipass": "^3.1.0",
        "minipass-sized": "^1.0.3",
        "minizlib": "^2.0.0"
      },
      "engines": {
        "node": ">=8"
      },
      "optionalDependencies": {
        "encoding": "^0.1.12"
      }
    },
    "node_modules/minipass-flush": {
      "version": "1.0.5",
      "resolved": "https://registry.npmjs.org/minipass-flush/-/minipass-flush-1.0.5.tgz",
      "integrity": "sha512-JmQSYYpPUqX5Jyn1mXaRwOda1uQ8HP5KAT/oDSLCzt1BYRhQU0/hDtsB1ufZfEEzMZ9aAVmsBw8+FWsIXlClWw==",
      "dev": true,
      "dependencies": {
        "minipass": "^3.0.0"
      },
      "engines": {
        "node": ">= 8"
      }
    },
    "node_modules/minipass-json-stream": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/minipass-json-stream/-/minipass-json-stream-1.0.1.tgz",
      "integrity": "sha512-ODqY18UZt/I8k+b7rl2AENgbWE8IDYam+undIJONvigAz8KR5GWblsFTEfQs0WODsjbSXWlm+JHEv8Gr6Tfdbg==",
      "dev": true,
      "dependencies": {
        "jsonparse": "^1.3.1",
        "minipass": "^3.0.0"
      }
    },
    "node_modules/minipass-pipeline": {
      "version": "1.2.4",
      "resolved": "https://registry.npmjs.org/minipass-pipeline/-/minipass-pipeline-1.2.4.tgz",
      "integrity": "sha512-xuIq7cIOt09RPRJ19gdi4b+RiNvDFYe5JH+ggNvBqGqpQXcru3PcRmOZuHBKWK1Txf9+cQ+HMVN4d6z46LZP7A==",
      "dev": true,
      "dependencies": {
        "minipass": "^3.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/minipass-sized": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/minipass-sized/-/minipass-sized-1.0.3.tgz",
      "integrity": "sha512-MbkQQ2CTiBMlA2Dm/5cY+9SWFEN8pzzOXi6rlM5Xxq0Yqbda5ZQy9sU75a673FE9ZK0Zsbr6Y5iP6u9nktfg2g==",
      "dev": true,
      "dependencies": {
        "minipass": "^3.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/minizlib": {
      "version": "2.1.2",
      "resolved": "https://registry.npmjs.org/minizlib/-/minizlib-2.1.2.tgz",
      "integrity": "sha512-bAxsR8BVfj60DWXHE3u30oHzfl4G7khkSuPW+qvpd7jFRHm7dLxOjUk1EHACJ/hxLY8phGJ0YhYHZo7jil7Qdg==",
      "dev": true,
      "dependencies": {
        "minipass": "^3.0.0",
        "yallist": "^4.0.0"
      },
      "engines": {
        "node": ">= 8"
      }
    },
    "node_modules/mkdirp": {
      "version": "1.0.4",
      "resolved": "https://registry.npmjs.org/mkdirp/-/mkdirp-1.0.4.tgz",
      "integrity": "sha512-vVqVZQyf3WLx2Shd0qJ9xuvqgAyKPLAiqITEtqW0oIUjzo3PePDd6fW9iFz30ef7Ysp/oiWqbhszeGWW2T6Gzw==",
      "dev": true,
      "bin": {
        "mkdirp": "bin/cmd.js"
      },
      "engines": {
        "node": ">=10"
      }
    },
    "node_modules/morgan": {
      "version": "1.10.0",
      "resolved": "https://registry.npmjs.org/morgan/-/morgan-1.10.0.tgz",
      "integrity": "sha512-AbegBVI4sh6El+1gNwvD5YIck7nSA36weD7xvIxG4in80j/UoK8AEGaWnnz8v1GxonMCltmlNs5ZKbGvl9b1XQ==",
      "dependencies": {
        "basic-auth": "~2.0.1",
        "debug": "2.6.9",
        "depd": "~2.0.0",
        "on-finished": "~2.3.0",
        "on-headers": "~1.0.2"
      },
      "engines": {
        "node": ">= 0.8.0"
      }
    },
    "node_modules/morgan/node_modules/debug": {
      "version": "2.6.9",
      "resolved": "https://registry.npmjs.org/debug/-/debug-2.6.9.tgz",
      "integrity": "sha512-bC7ElrdJaJnPbAP+1EotYvqZsb3ecl5wi6Bfi6BJTUcNowp6cvspg0jXznRTKDjm/E7AdgFBVeAPVMNcKGsHMA==",
      "dependencies": {
        "ms": "2.0.0"
      }
    },
    "node_modules/morgan/node_modules/depd": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/depd/-/depd-2.0.0.tgz",
      "integrity": "sha512-g7nH6P6dyDioJogAAGprGpCtVImJhpPk/roCzdb3fIh61/s/nPsfR6onyMwkCAR/OlC3yBC0lESvUoQEAssIrw==",
      "engines": {
        "node": ">= 0.8"
      }
    },
    "node_modules/morgan/node_modules/ms": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/ms/-/ms-2.0.0.tgz",
      "integrity": "sha1-VgiurfwAvmwpAd9fmGF4jeDVl8g="
    },
    "node_modules/ms": {
      "version": "2.1.2",
      "resolved": "https://registry.npmjs.org/ms/-/ms-2.1.2.tgz",
      "integrity": "sha512-sGkPx+VjMtmA6MX27oA4FBFELFCZZ4S4XqeGOXCv68tT+jb3vk/RyaKWP0PTKyWtmLSM0b+adUTEvbs1PEaH2w=="
    },
    "node_modules/multicast-dns": {
      "version": "6.2.3",
      "resolved": "https://registry.npmjs.org/multicast-dns/-/multicast-dns-6.2.3.tgz",
      "integrity": "sha512-ji6J5enbMyGRHIAkAOu3WdV8nggqviKCEKtXcOqfphZZtQrmHKycfynJ2V7eVPUA4NhJ6V7Wf4TmGbTwKE9B6g==",
      "dev": true,
      "dependencies": {
        "dns-packet": "^1.3.1",
        "thunky": "^1.0.2"
      },
      "bin": {
        "multicast-dns": "cli.js"
      }
    },
    "node_modules/multicast-dns-service-types": {
      "version": "1.1.0",
      "resolved": "https://registry.npmjs.org/multicast-dns-service-types/-/multicast-dns-service-types-1.1.0.tgz",
      "integrity": "sha1-iZ8R2WhuXgXLkbNdXw5jt3PPyQE=",
      "dev": true
    },
    "node_modules/mute-stream": {
      "version": "0.0.8",
      "resolved": "https://registry.npmjs.org/mute-stream/-/mute-stream-0.0.8.tgz",
      "integrity": "sha512-nnbWWOkoWyUsTjKrhgD0dcz22mdkSnpYqbEjIm2nhwhuxlSkpywJmBo8h0ZqJdkp73mb90SssHkN4rsRaBAfAA==",
      "dev": true
    },
    "node_modules/nanoid": {
      "version": "3.2.0",
      "resolved": "https://registry.npmjs.org/nanoid/-/nanoid-3.2.0.tgz",
      "integrity": "sha512-fmsZYa9lpn69Ad5eDn7FMcnnSR+8R34W9qJEijxYhTbfOWzr22n1QxCMzXLK+ODyW2973V3Fux959iQoUxzUIA==",
      "bin": {
        "nanoid": "bin/nanoid.cjs"
      },
      "engines": {
        "node": "^10 || ^12 || ^13.7 || ^14 || >=15.0.1"
      }
    },
    "node_modules/needle": {
      "version": "2.9.1",
      "resolved": "https://registry.npmjs.org/needle/-/needle-2.9.1.tgz",
      "integrity": "sha512-6R9fqJ5Zcmf+uYaFgdIHmLwNldn5HbK8L5ybn7Uz+ylX/rnOsSp1AHcvQSrCaFN+qNM1wpymHqD7mVasEOlHGQ==",
      "dev": true,
      "optional": true,
      "dependencies": {
        "debug": "^3.2.6",
        "iconv-lite": "^0.4.4",
        "sax": "^1.2.4"
      },
      "bin": {
        "needle": "bin/needle"
      },
      "engines": {
        "node": ">= 4.4.x"
      }
    },
    "node_modules/needle/node_modules/debug": {
      "version": "3.2.7",
      "resolved": "https://registry.npmjs.org/debug/-/debug-3.2.7.tgz",
      "integrity": "sha512-CFjzYYAi4ThfiQvizrFQevTTXHtnCqWfe7x1AhgEscTz6ZbLbfoLRLPugTQyBth6f8ZERVUSyWHFD/7Wu4t1XQ==",
      "dev": true,
      "optional": true,
      "dependencies": {
        "ms": "^2.1.1"
      }
    },
    "node_modules/negotiator": {
      "version": "0.6.3",
      "resolved": "https://registry.npmjs.org/negotiator/-/negotiator-0.6.3.tgz",
      "integrity": "sha512-+EUsqGPLsM+j/zdChZjsnX51g4XrHFOIXwfnCVPGlQk/k5giakcKsuxCObBRu6DSm9opw/O6slWbJdghQM4bBg==",
      "dev": true,
      "engines": {
        "node": ">= 0.6"
      }
    },
    "node_modules/neo-async": {
      "version": "2.6.2",
      "resolved": "https://registry.npmjs.org/neo-async/-/neo-async-2.6.2.tgz",
      "integrity": "sha512-Yd3UES5mWCSqR+qNT93S3UoYUkqAZ9lLg8a7g9rimsWmYGK8cVToA4/sF3RrshdyV3sAGMXVUmpMYOw+dLpOuw==",
      "dev": true
    },
    "node_modules/nice-napi": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/nice-napi/-/nice-napi-1.0.2.tgz",
      "integrity": "sha512-px/KnJAJZf5RuBGcfD+Sp2pAKq0ytz8j+1NehvgIGFkvtvFrDM3T8E4x/JJODXK9WZow8RRGrbA9QQ3hs+pDhA==",
      "dev": true,
      "hasInstallScript": true,
      "optional": true,
      "os": [
        "!win32"
      ],
      "dependencies": {
        "node-addon-api": "^3.0.0",
        "node-gyp-build": "^4.2.2"
      }
    },
    "node_modules/node-addon-api": {
      "version": "3.2.1",
      "resolved": "https://registry.npmjs.org/node-addon-api/-/node-addon-api-3.2.1.tgz",
      "integrity": "sha512-mmcei9JghVNDYydghQmeDX8KoAm0FAiYyIcUt/N4nhyAipB17pllZQDOJD2fotxABnt4Mdz+dKTO7eftLg4d0A==",
      "dev": true,
      "optional": true
    },
    "node_modules/node-forge": {
      "version": "0.10.0",
      "resolved": "https://registry.npmjs.org/node-forge/-/node-forge-0.10.0.tgz",
      "integrity": "sha512-PPmu8eEeG9saEUvI97fm4OYxXVB6bFvyNTyiUOBichBpFG8A1Ljw3bY62+5oOjDEMHRnd0Y7HQ+x7uzxOzC6JA==",
      "dev": true,
      "engines": {
        "node": ">= 6.0.0"
      }
    },
    "node_modules/node-gyp": {
      "version": "8.4.1",
      "resolved": "https://registry.npmjs.org/node-gyp/-/node-gyp-8.4.1.tgz",
      "integrity": "sha512-olTJRgUtAb/hOXG0E93wZDs5YiJlgbXxTwQAFHyNlRsXQnYzUaF2aGgujZbw+hR8aF4ZG/rST57bWMWD16jr9w==",
      "dev": true,
      "dependencies": {
        "env-paths": "^2.2.0",
        "glob": "^7.1.4",
        "graceful-fs": "^4.2.6",
        "make-fetch-happen": "^9.1.0",
        "nopt": "^5.0.0",
        "npmlog": "^6.0.0",
        "rimraf": "^3.0.2",
        "semver": "^7.3.5",
        "tar": "^6.1.2",
        "which": "^2.0.2"
      },
      "bin": {
        "node-gyp": "bin/node-gyp.js"
      },
      "engines": {
        "node": ">= 10.12.0"
      }
    },
    "node_modules/node-gyp-build": {
      "version": "4.3.0",
      "resolved": "https://registry.npmjs.org/node-gyp-build/-/node-gyp-build-4.3.0.tgz",
      "integrity": "sha512-iWjXZvmboq0ja1pUGULQBexmxq8CV4xBhX7VDOTbL7ZR4FOowwY/VOtRxBN/yKxmdGoIp4j5ysNT4u3S2pDQ3Q==",
      "dev": true,
      "optional": true,
      "bin": {
        "node-gyp-build": "bin.js",
        "node-gyp-build-optional": "optional.js",
        "node-gyp-build-test": "build-test.js"
      }
    },
    "node_modules/node-gyp/node_modules/which": {
      "version": "2.0.2",
      "resolved": "https://registry.npmjs.org/which/-/which-2.0.2.tgz",
      "integrity": "sha512-BLI3Tl1TW3Pvl70l3yq3Y64i+awpwXqsGBYWkkqMtnbXgrMD+yj7rhW0kuEDxzJaYXGjEW5ogapKNMEKNMjibA==",
      "dev": true,
      "dependencies": {
        "isexe": "^2.0.0"
      },
      "bin": {
        "node-which": "bin/node-which"
      },
      "engines": {
        "node": ">= 8"
      }
    },
    "node_modules/node-releases": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/node-releases/-/node-releases-2.0.1.tgz",
      "integrity": "sha512-CqyzN6z7Q6aMeF/ktcMVTzhAHCEpf8SOarwpzpf8pNBY2k5/oM34UHldUwp8VKI7uxct2HxSRdJjBaZeESzcxA==",
      "dev": true
    },
    "node_modules/nopt": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/nopt/-/nopt-5.0.0.tgz",
      "integrity": "sha512-Tbj67rffqceeLpcRXrT7vKAN8CwfPeIBgM7E6iBkmKLV7bEMwpGgYLGv0jACUsECaa/vuxP0IjEont6umdMgtQ==",
      "dev": true,
      "dependencies": {
        "abbrev": "1"
      },
      "bin": {
        "nopt": "bin/nopt.js"
      },
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/normalize-path": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/normalize-path/-/normalize-path-3.0.0.tgz",
      "integrity": "sha512-6eZs5Ls3WtCisHWp9S2GUy8dqkpGi4BVSz3GaqiE6ezub0512ESztXUwUB6C6IKbQkY2Pnb/mD4WYojCRwcwLA==",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/normalize-range": {
      "version": "0.1.2",
      "resolved": "https://registry.npmjs.org/normalize-range/-/normalize-range-0.1.2.tgz",
      "integrity": "sha1-LRDAa9/TEuqXd2laTShDlFa3WUI=",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/normalize-url": {
      "version": "4.5.1",
      "resolved": "https://registry.npmjs.org/normalize-url/-/normalize-url-4.5.1.tgz",
      "integrity": "sha512-9UZCFRHQdNrfTpGg8+1INIg93B6zE0aXMVFkw1WFwvO4SlZywU6aLg5Of0Ap/PgcbSw4LNxvMWXMeugwMCX0AA==",
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/npm-bundled": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/npm-bundled/-/npm-bundled-1.1.2.tgz",
      "integrity": "sha512-x5DHup0SuyQcmL3s7Rx/YQ8sbw/Hzg0rj48eN0dV7hf5cmQq5PXIeioroH3raV1QC1yh3uTYuMThvEQF3iKgGQ==",
      "dev": true,
      "dependencies": {
        "npm-normalize-package-bin": "^1.0.1"
      }
    },
    "node_modules/npm-install-checks": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/npm-install-checks/-/npm-install-checks-4.0.0.tgz",
      "integrity": "sha512-09OmyDkNLYwqKPOnbI8exiOZU2GVVmQp7tgez2BPi5OZC8M82elDAps7sxC4l//uSUtotWqoEIDwjRvWH4qz8w==",
      "dev": true,
      "dependencies": {
        "semver": "^7.1.1"
      },
      "engines": {
        "node": ">=10"
      }
    },
    "node_modules/npm-normalize-package-bin": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/npm-normalize-package-bin/-/npm-normalize-package-bin-1.0.1.tgz",
      "integrity": "sha512-EPfafl6JL5/rU+ot6P3gRSCpPDW5VmIzX959Ob1+ySFUuuYHWHekXpwdUZcKP5C+DS4GEtdJluwBjnsNDl+fSA==",
      "dev": true
    },
    "node_modules/npm-package-arg": {
      "version": "8.1.5",
      "resolved": "https://registry.npmjs.org/npm-package-arg/-/npm-package-arg-8.1.5.tgz",
      "integrity": "sha512-LhgZrg0n0VgvzVdSm1oiZworPbTxYHUJCgtsJW8mGvlDpxTM1vSJc3m5QZeUkhAHIzbz3VCHd/R4osi1L1Tg/Q==",
      "dev": true,
      "dependencies": {
        "hosted-git-info": "^4.0.1",
        "semver": "^7.3.4",
        "validate-npm-package-name": "^3.0.0"
      },
      "engines": {
        "node": ">=10"
      }
    },
    "node_modules/npm-packlist": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/npm-packlist/-/npm-packlist-3.0.0.tgz",
      "integrity": "sha512-L/cbzmutAwII5glUcf2DBRNY/d0TFd4e/FnaZigJV6JD85RHZXJFGwCndjMWiiViiWSsWt3tiOLpI3ByTnIdFQ==",
      "dev": true,
      "dependencies": {
        "glob": "^7.1.6",
        "ignore-walk": "^4.0.1",
        "npm-bundled": "^1.1.1",
        "npm-normalize-package-bin": "^1.0.1"
      },
      "bin": {
        "npm-packlist": "bin/index.js"
      },
      "engines": {
        "node": ">=10"
      }
    },
    "node_modules/npm-pick-manifest": {
      "version": "6.1.1",
      "resolved": "https://registry.npmjs.org/npm-pick-manifest/-/npm-pick-manifest-6.1.1.tgz",
      "integrity": "sha512-dBsdBtORT84S8V8UTad1WlUyKIY9iMsAmqxHbLdeEeBNMLQDlDWWra3wYUx9EBEIiG/YwAy0XyNHDd2goAsfuA==",
      "dev": true,
      "dependencies": {
        "npm-install-checks": "^4.0.0",
        "npm-normalize-package-bin": "^1.0.1",
        "npm-package-arg": "^8.1.2",
        "semver": "^7.3.4"
      }
    },
    "node_modules/npm-registry-fetch": {
      "version": "11.0.0",
      "resolved": "https://registry.npmjs.org/npm-registry-fetch/-/npm-registry-fetch-11.0.0.tgz",
      "integrity": "sha512-jmlgSxoDNuhAtxUIG6pVwwtz840i994dL14FoNVZisrmZW5kWd63IUTNv1m/hyRSGSqWjCUp/YZlS1BJyNp9XA==",
      "dev": true,
      "dependencies": {
        "make-fetch-happen": "^9.0.1",
        "minipass": "^3.1.3",
        "minipass-fetch": "^1.3.0",
        "minipass-json-stream": "^1.0.1",
        "minizlib": "^2.0.0",
        "npm-package-arg": "^8.0.0"
      },
      "engines": {
        "node": ">=10"
      }
    },
    "node_modules/npm-run-path": {
      "version": "4.0.1",
      "resolved": "https://registry.npmjs.org/npm-run-path/-/npm-run-path-4.0.1.tgz",
      "integrity": "sha512-S48WzZW777zhNIrn7gxOlISNAqi9ZC/uQFnRdbeIHhZhCA6UqpkOT8T1G7BvfdgP4Er8gF4sUbaS0i7QvIfCWw==",
      "dev": true,
      "dependencies": {
        "path-key": "^3.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/npmlog": {
      "version": "6.0.0",
      "resolved": "https://registry.npmjs.org/npmlog/-/npmlog-6.0.0.tgz",
      "integrity": "sha512-03ppFRGlsyUaQFbGC2C8QWJN/C/K7PsfyD9aQdhVKAQIH4sQBc8WASqFBP7O+Ut4d2oo5LoeoboB3cGdBZSp6Q==",
      "dev": true,
      "dependencies": {
        "are-we-there-yet": "^2.0.0",
        "console-control-strings": "^1.1.0",
        "gauge": "^4.0.0",
        "set-blocking": "^2.0.0"
      },
      "engines": {
        "node": "^12.13.0 || ^14.15.0 || >=16"
      }
    },
    "node_modules/nth-check": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/nth-check/-/nth-check-2.0.1.tgz",
      "integrity": "sha512-it1vE95zF6dTT9lBsYbxvqh0Soy4SPowchj0UBGj/V6cTPnXXtQOPUbhZ6CmGzAD/rW22LQK6E96pcdJXk4A4w==",
      "dev": true,
      "dependencies": {
        "boolbase": "^1.0.0"
      },
      "funding": {
        "url": "https://github.com/fb55/nth-check?sponsor=1"
      }
    },
    "node_modules/object-assign": {
      "version": "4.1.1",
      "resolved": "https://registry.npmjs.org/object-assign/-/object-assign-4.1.1.tgz",
      "integrity": "sha1-IQmtx5ZYh8/AXLvUQsrIv7s2CGM=",
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/object-is": {
      "version": "1.1.5",
      "resolved": "https://registry.npmjs.org/object-is/-/object-is-1.1.5.tgz",
      "integrity": "sha512-3cyDsyHgtmi7I7DfSSI2LDp6SK2lwvtbg0p0R1e0RvTqF5ceGx+K2dfSjm1bKDMVCFEDAQvy+o8c6a7VujOddw==",
      "dev": true,
      "dependencies": {
        "call-bind": "^1.0.2",
        "define-properties": "^1.1.3"
      },
      "engines": {
        "node": ">= 0.4"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/object-keys": {
      "version": "1.1.1",
      "resolved": "https://registry.npmjs.org/object-keys/-/object-keys-1.1.1.tgz",
      "integrity": "sha512-NuAESUOUMrlIXOfHKzD6bpPu3tYt3xvjNdRIQ+FeT0lNb4K8WR70CaDxhuNguS2XG+GjkyMwOzsN5ZktImfhLA==",
      "dev": true,
      "engines": {
        "node": ">= 0.4"
      }
    },
    "node_modules/object.assign": {
      "version": "4.1.2",
      "resolved": "https://registry.npmjs.org/object.assign/-/object.assign-4.1.2.tgz",
      "integrity": "sha512-ixT2L5THXsApyiUPYKmW+2EHpXXe5Ii3M+f4e+aJFAHao5amFRW6J0OO6c/LU8Be47utCx2GL89hxGB6XSmKuQ==",
      "dev": true,
      "dependencies": {
        "call-bind": "^1.0.0",
        "define-properties": "^1.1.3",
        "has-symbols": "^1.0.1",
        "object-keys": "^1.1.1"
      },
      "engines": {
        "node": ">= 0.4"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/obuf": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/obuf/-/obuf-1.1.2.tgz",
      "integrity": "sha512-PX1wu0AmAdPqOL1mWhqmlOd8kOIZQwGZw6rh7uby9fTc5lhaOWFLX3I6R1hrF9k3zUY40e6igsLGkDXK92LJNg==",
      "dev": true
    },
    "node_modules/on-finished": {
      "version": "2.3.0",
      "resolved": "https://registry.npmjs.org/on-finished/-/on-finished-2.3.0.tgz",
      "integrity": "sha1-IPEzZIGwg811M3mSoWlxqi2QaUc=",
      "dependencies": {
        "ee-first": "1.1.1"
      },
      "engines": {
        "node": ">= 0.8"
      }
    },
    "node_modules/on-headers": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/on-headers/-/on-headers-1.0.2.tgz",
      "integrity": "sha512-pZAE+FJLoyITytdqK0U5s+FIpjN0JP3OzFi/u8Rx+EV5/W+JTWGXG8xFzevE7AjBfDqHv/8vL8qQsIhHnqRkrA==",
      "engines": {
        "node": ">= 0.8"
      }
    },
    "node_modules/once": {
      "version": "1.4.0",
      "resolved": "https://registry.npmjs.org/once/-/once-1.4.0.tgz",
      "integrity": "sha1-WDsap3WWHUsROsF9nFC6753Xa9E=",
      "dependencies": {
        "wrappy": "1"
      }
    },
    "node_modules/onetime": {
      "version": "5.1.2",
      "resolved": "https://registry.npmjs.org/onetime/-/onetime-5.1.2.tgz",
      "integrity": "sha512-kbpaSSGJTWdAY5KPVeMOKXSrPtr8C8C7wodJbcsd51jRnmD+GZu8Y0VoU6Dm5Z4vWr0Ig/1NKuWRKf7j5aaYSg==",
      "dev": true,
      "dependencies": {
        "mimic-fn": "^2.1.0"
      },
      "engines": {
        "node": ">=6"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/open": {
      "version": "8.4.0",
      "resolved": "https://registry.npmjs.org/open/-/open-8.4.0.tgz",
      "integrity": "sha512-XgFPPM+B28FtCCgSb9I+s9szOC1vZRSwgWsRUA5ylIxRTgKozqjOCrVOqGsYABPYK5qnfqClxZTFBa8PKt2v6Q==",
      "dev": true,
      "dependencies": {
        "define-lazy-prop": "^2.0.0",
        "is-docker": "^2.1.1",
        "is-wsl": "^2.2.0"
      },
      "engines": {
        "node": ">=12"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/ora": {
      "version": "5.4.1",
      "resolved": "https://registry.npmjs.org/ora/-/ora-5.4.1.tgz",
      "integrity": "sha512-5b6Y85tPxZZ7QytO+BQzysW31HJku27cRIlkbAXaNx+BdcVi+LlRFmVXzeF6a7JCwJpyw5c4b+YSVImQIrBpuQ==",
      "dev": true,
      "dependencies": {
        "bl": "^4.1.0",
        "chalk": "^4.1.0",
        "cli-cursor": "^3.1.0",
        "cli-spinners": "^2.5.0",
        "is-interactive": "^1.0.0",
        "is-unicode-supported": "^0.1.0",
        "log-symbols": "^4.1.0",
        "strip-ansi": "^6.0.0",
        "wcwidth": "^1.0.1"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/ora/node_modules/ansi-styles": {
      "version": "4.3.0",
      "resolved": "https://registry.npmjs.org/ansi-styles/-/ansi-styles-4.3.0.tgz",
      "integrity": "sha512-zbB9rCJAT1rbjiVDb2hqKFHNYLxgtk8NURxZ3IZwD3F6NtxbXZQCnnSi1Lkx+IDohdPlFp222wVALIheZJQSEg==",
      "dev": true,
      "dependencies": {
        "color-convert": "^2.0.1"
      },
      "engines": {
        "node": ">=8"
      },
      "funding": {
        "url": "https://github.com/chalk/ansi-styles?sponsor=1"
      }
    },
    "node_modules/ora/node_modules/chalk": {
      "version": "4.1.2",
      "resolved": "https://registry.npmjs.org/chalk/-/chalk-4.1.2.tgz",
      "integrity": "sha512-oKnbhFyRIXpUuez8iBMmyEa4nbj4IOQyuhc/wy9kY7/WVPcwIO9VA668Pu8RkO7+0G76SLROeyw9CpQ061i4mA==",
      "dev": true,
      "dependencies": {
        "ansi-styles": "^4.1.0",
        "supports-color": "^7.1.0"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/chalk/chalk?sponsor=1"
      }
    },
    "node_modules/ora/node_modules/color-convert": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/color-convert/-/color-convert-2.0.1.tgz",
      "integrity": "sha512-RRECPsj7iu/xb5oKYcsFHSppFNnsj/52OVTRKb4zP5onXwVF3zVmmToNcOfGC+CRDpfK/U584fMg38ZHCaElKQ==",
      "dev": true,
      "dependencies": {
        "color-name": "~1.1.4"
      },
      "engines": {
        "node": ">=7.0.0"
      }
    },
    "node_modules/ora/node_modules/color-name": {
      "version": "1.1.4",
      "resolved": "https://registry.npmjs.org/color-name/-/color-name-1.1.4.tgz",
      "integrity": "sha512-dOy+3AuW3a2wNbZHIuMZpTcgjGuLU/uBL/ubcZF9OXbDo8ff4O8yVp5Bf0efS8uEoYo5q4Fx7dY9OgQGXgAsQA==",
      "dev": true
    },
    "node_modules/ora/node_modules/has-flag": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/has-flag/-/has-flag-4.0.0.tgz",
      "integrity": "sha512-EykJT/Q1KjTWctppgIAgfSO0tKVuZUjhgMr17kqTumMl6Afv3EISleU7qZUzoXDFTAHTDC4NOoG/ZxU3EvlMPQ==",
      "dev": true,
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/ora/node_modules/supports-color": {
      "version": "7.2.0",
      "resolved": "https://registry.npmjs.org/supports-color/-/supports-color-7.2.0.tgz",
      "integrity": "sha512-qpCAvRl9stuOHveKsn7HncJRvv501qIacKzQlO/+Lwxc9+0q2wLyv4Dfvt80/DPn2pqOBsJdDiogXGR9+OvwRw==",
      "dev": true,
      "dependencies": {
        "has-flag": "^4.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/os-tmpdir": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/os-tmpdir/-/os-tmpdir-1.0.2.tgz",
      "integrity": "sha1-u+Z0BseaqFxc/sdm/lc0VV36EnQ=",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/p-cancelable": {
      "version": "1.1.0",
      "resolved": "https://registry.npmjs.org/p-cancelable/-/p-cancelable-1.1.0.tgz",
      "integrity": "sha512-s73XxOZ4zpt1edZYZzvhqFa6uvQc1vwUa0K0BdtIZgQMAJj9IbebH+JkgKZc9h+B05PKHLOTl4ajG1BmNrVZlw==",
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/p-limit": {
      "version": "2.3.0",
      "resolved": "https://registry.npmjs.org/p-limit/-/p-limit-2.3.0.tgz",
      "integrity": "sha512-//88mFWSJx8lxCzwdAABTJL2MyWB12+eIY7MDL2SqLmAkeKU9qxRvWuSyTjm3FUmpBEMuFfckAIqEaVGUDxb6w==",
      "dev": true,
      "dependencies": {
        "p-try": "^2.0.0"
      },
      "engines": {
        "node": ">=6"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/p-locate": {
      "version": "4.1.0",
      "resolved": "https://registry.npmjs.org/p-locate/-/p-locate-4.1.0.tgz",
      "integrity": "sha512-R79ZZ/0wAxKGu3oYMlz8jy/kbhsNrS7SKZ7PxEHBgJ5+F2mtFW2fK2cOtBh1cHYkQsbzFV7I+EoRKe6Yt0oK7A==",
      "dev": true,
      "dependencies": {
        "p-limit": "^2.2.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/p-map": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/p-map/-/p-map-4.0.0.tgz",
      "integrity": "sha512-/bjOqmgETBYB5BoEeGVea8dmvHb2m9GLy1E9W43yeyfP6QQCZGFNa+XRceJEuDB6zqr+gKpIAmlLebMpykw/MQ==",
      "dev": true,
      "dependencies": {
        "aggregate-error": "^3.0.0"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/p-retry": {
      "version": "4.6.1",
      "resolved": "https://registry.npmjs.org/p-retry/-/p-retry-4.6.1.tgz",
      "integrity": "sha512-e2xXGNhZOZ0lfgR9kL34iGlU8N/KO0xZnQxVEwdeOvpqNDQfdnxIYizvWtK8RglUa3bGqI8g0R/BdfzLMxRkiA==",
      "dev": true,
      "dependencies": {
        "@types/retry": "^0.12.0",
        "retry": "^0.13.1"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/p-retry/node_modules/retry": {
      "version": "0.13.1",
      "resolved": "https://registry.npmjs.org/retry/-/retry-0.13.1.tgz",
      "integrity": "sha512-XQBQ3I8W1Cge0Seh+6gjj03LbmRFWuoszgK9ooCpwYIrhhoO80pfq4cUkU5DkknwfOfFteRwlZ56PYOGYyFWdg==",
      "dev": true,
      "engines": {
        "node": ">= 4"
      }
    },
    "node_modules/p-try": {
      "version": "2.2.0",
      "resolved": "https://registry.npmjs.org/p-try/-/p-try-2.2.0.tgz",
      "integrity": "sha512-R4nPAVTAU0B9D35/Gk3uJf/7XYbQcyohSKdvAxIRSNghFl4e71hVoGnBNQz9cWaXxO2I10KTC+3jMdvvoKw6dQ==",
      "dev": true,
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/package-json": {
      "version": "6.5.0",
      "resolved": "https://registry.npmjs.org/package-json/-/package-json-6.5.0.tgz",
      "integrity": "sha512-k3bdm2n25tkyxcjSKzB5x8kfVxlMdgsbPr0GkZcwHsLpba6cBjqCt1KlcChKEvxHIcTB1FVMuwoijZ26xex5MQ==",
      "dependencies": {
        "got": "^9.6.0",
        "registry-auth-token": "^4.0.0",
        "registry-url": "^5.0.0",
        "semver": "^6.2.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/package-json/node_modules/semver": {
      "version": "6.3.0",
      "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.0.tgz",
      "integrity": "sha512-b39TBaTSfV6yBrapU89p5fKekE2m/NwnDocOVruQFS1/veMgdzuPcnOM34M6CwxW8jH/lxEa5rBoDeUwu5HHTw==",
      "bin": {
        "semver": "bin/semver.js"
      }
    },
    "node_modules/pacote": {
      "version": "12.0.2",
      "resolved": "https://registry.npmjs.org/pacote/-/pacote-12.0.2.tgz",
      "integrity": "sha512-Ar3mhjcxhMzk+OVZ8pbnXdb0l8+pimvlsqBGRNkble2NVgyqOGE3yrCGi/lAYq7E7NRDMz89R1Wx5HIMCGgeYg==",
      "dev": true,
      "dependencies": {
        "@npmcli/git": "^2.1.0",
        "@npmcli/installed-package-contents": "^1.0.6",
        "@npmcli/promise-spawn": "^1.2.0",
        "@npmcli/run-script": "^2.0.0",
        "cacache": "^15.0.5",
        "chownr": "^2.0.0",
        "fs-minipass": "^2.1.0",
        "infer-owner": "^1.0.4",
        "minipass": "^3.1.3",
        "mkdirp": "^1.0.3",
        "npm-package-arg": "^8.0.1",
        "npm-packlist": "^3.0.0",
        "npm-pick-manifest": "^6.0.0",
        "npm-registry-fetch": "^11.0.0",
        "promise-retry": "^2.0.1",
        "read-package-json-fast": "^2.0.1",
        "rimraf": "^3.0.2",
        "ssri": "^8.0.1",
        "tar": "^6.1.0"
      },
      "bin": {
        "pacote": "lib/bin.js"
      },
      "engines": {
        "node": "^12.13.0 || ^14.15.0 || >=16"
      }
    },
    "node_modules/pako": {
      "version": "1.0.11",
      "resolved": "https://registry.npmjs.org/pako/-/pako-1.0.11.tgz",
      "integrity": "sha512-4hLB8Py4zZce5s4yd9XzopqwVv/yGNhV1Bl8NTmCq1763HeK2+EwVTv+leGeL13Dnh2wfbqowVPXCIO0z4taYw==",
      "dev": true
    },
    "node_modules/parent-module": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/parent-module/-/parent-module-1.0.1.tgz",
      "integrity": "sha512-GQ2EWRpQV8/o+Aw8YqtfZZPfNRWZYkbidE9k5rpl/hC3vtHHBfGm2Ifi6qWV+coDGkrUKZAxE3Lot5kcsRlh+g==",
      "dev": true,
      "dependencies": {
        "callsites": "^3.0.0"
      },
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/parse-json": {
      "version": "5.2.0",
      "resolved": "https://registry.npmjs.org/parse-json/-/parse-json-5.2.0.tgz",
      "integrity": "sha512-ayCKvm/phCGxOkYRSCM82iDwct8/EonSEgCSxWxD7ve6jHggsFl4fZVQBPRNgQoKiuV/odhFrGzQXZwbifC8Rg==",
      "dev": true,
      "dependencies": {
        "@babel/code-frame": "^7.0.0",
        "error-ex": "^1.3.1",
        "json-parse-even-better-errors": "^2.3.0",
        "lines-and-columns": "^1.1.6"
      },
      "engines": {
        "node": ">=8"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/parse-node-version": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/parse-node-version/-/parse-node-version-1.0.1.tgz",
      "integrity": "sha512-3YHlOa/JgH6Mnpr05jP9eDG254US9ek25LyIxZlDItp2iJtwyaXQb57lBYLdT3MowkUFYEV2XXNAYIPlESvJlA==",
      "dev": true,
      "engines": {
        "node": ">= 0.10"
      }
    },
    "node_modules/parse5": {
      "version": "6.0.1",
      "resolved": "https://registry.npmjs.org/parse5/-/parse5-6.0.1.tgz",
      "integrity": "sha512-Ofn/CTFzRGTTxwpNEs9PP93gXShHcTq255nzRYSKe8AkVpZY7e1fpmTfOyoIvjP5HG7Z2ZM7VS9PPhQGW2pOpw==",
      "dev": true
    },
    "node_modules/parse5-html-rewriting-stream": {
      "version": "6.0.1",
      "resolved": "https://registry.npmjs.org/parse5-html-rewriting-stream/-/parse5-html-rewriting-stream-6.0.1.tgz",
      "integrity": "sha512-vwLQzynJVEfUlURxgnf51yAJDQTtVpNyGD8tKi2Za7m+akukNHxCcUQMAa/mUGLhCeicFdpy7Tlvj8ZNKadprg==",
      "dev": true,
      "dependencies": {
        "parse5": "^6.0.1",
        "parse5-sax-parser": "^6.0.1"
      }
    },
    "node_modules/parse5-htmlparser2-tree-adapter": {
      "version": "6.0.1",
      "resolved": "https://registry.npmjs.org/parse5-htmlparser2-tree-adapter/-/parse5-htmlparser2-tree-adapter-6.0.1.tgz",
      "integrity": "sha512-qPuWvbLgvDGilKc5BoicRovlT4MtYT6JfJyBOMDsKoiT+GiuP5qyrPCnR9HcPECIJJmZh5jRndyNThnhhb/vlA==",
      "dev": true,
      "dependencies": {
        "parse5": "^6.0.1"
      }
    },
    "node_modules/parse5-sax-parser": {
      "version": "6.0.1",
      "resolved": "https://registry.npmjs.org/parse5-sax-parser/-/parse5-sax-parser-6.0.1.tgz",
      "integrity": "sha512-kXX+5S81lgESA0LsDuGjAlBybImAChYRMT+/uKCEXFBFOeEhS52qUCydGhU3qLRD8D9DVjaUo821WK7DM4iCeg==",
      "dev": true,
      "dependencies": {
        "parse5": "^6.0.1"
      }
    },
    "node_modules/parseurl": {
      "version": "1.3.3",
      "resolved": "https://registry.npmjs.org/parseurl/-/parseurl-1.3.3.tgz",
      "integrity": "sha512-CiyeOxFT/JZyN5m0z9PfXw4SCBJ6Sygz1Dpl0wqjlhDEGGBP1GnsUVEL0p63hoG1fcj3fHynXi9NYO4nWOL+qQ==",
      "engines": {
        "node": ">= 0.8"
      }
    },
    "node_modules/path-exists": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/path-exists/-/path-exists-4.0.0.tgz",
      "integrity": "sha512-ak9Qy5Q7jYb2Wwcey5Fpvg2KoAc/ZIhLSLOSBmRmygPsGwkVVt0fZa0qrtMz+m6tJTAHfZQ8FnmB4MG4LWy7/w==",
      "dev": true,
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/path-is-absolute": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/path-is-absolute/-/path-is-absolute-1.0.1.tgz",
      "integrity": "sha1-F0uSaHNVNP+8es5r9TpanhtcX18=",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/path-key": {
      "version": "3.1.1",
      "resolved": "https://registry.npmjs.org/path-key/-/path-key-3.1.1.tgz",
      "integrity": "sha512-ojmeN0qd+y0jszEtoY48r0Peq5dwMEkIlCOu6Q5f41lfkswXuKtYrhgoTpLnyIcHm24Uhqx+5Tqm2InSwLhE6Q==",
      "dev": true,
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/path-parse": {
      "version": "1.0.7",
      "resolved": "https://registry.npmjs.org/path-parse/-/path-parse-1.0.7.tgz",
      "integrity": "sha512-LDJzPVEEEPR+y48z93A0Ed0yXb8pAByGWo/k5YYdYgpY2/2EsOsksJrq7lOHxryrVOn1ejG6oAp8ahvOIQD8sw==",
      "dev": true
    },
    "node_modules/path-to-regexp": {
      "version": "0.1.7",
      "resolved": "https://registry.npmjs.org/path-to-regexp/-/path-to-regexp-0.1.7.tgz",
      "integrity": "sha1-32BBeABfUi8V60SQ5yR6G/qmf4w="
    },
    "node_modules/path-type": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/path-type/-/path-type-4.0.0.tgz",
      "integrity": "sha512-gDKb8aZMDeD/tZWs9P6+q0J9Mwkdl6xMV8TjnGP3qJVJ06bdMgkbBlLU8IdfOsIsFz2BW1rNVT3XuNEl8zPAvw==",
      "dev": true,
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/picocolors": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/picocolors/-/picocolors-1.0.0.tgz",
      "integrity": "sha512-1fygroTLlHu66zi26VoTDv8yRgm0Fccecssto+MhsZ0D/DGW2sm8E8AjW7NU5VVTRt5GxbeZ5qBuJr+HyLYkjQ==",
      "dev": true
    },
    "node_modules/picomatch": {
      "version": "2.3.1",
      "resolved": "https://registry.npmjs.org/picomatch/-/picomatch-2.3.1.tgz",
      "integrity": "sha512-JU3teHTNjmE2VCGFzuY8EXzCDVwEqB2a8fsIvwaStHhAWJEeVd1o1QD80CU6+ZdEXXSLbSsuLwJjkCBWqRQUVA==",
      "dev": true,
      "engines": {
        "node": ">=8.6"
      },
      "funding": {
        "url": "https://github.com/sponsors/jonschlinkert"
      }
    },
    "node_modules/pify": {
      "version": "2.3.0",
      "resolved": "https://registry.npmjs.org/pify/-/pify-2.3.0.tgz",
      "integrity": "sha1-7RQaasBDqEnqWISY59yosVMw6Qw=",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/piscina": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/piscina/-/piscina-3.1.0.tgz",
      "integrity": "sha512-KTW4sjsCD34MHrUbx9eAAbuUSpVj407hQSgk/6Epkg0pbRBmv4a3UX7Sr8wxm9xYqQLnsN4mFOjqGDzHAdgKQg==",
      "dev": true,
      "dependencies": {
        "eventemitter-asyncresource": "^1.0.0",
        "hdr-histogram-js": "^2.0.1",
        "hdr-histogram-percentiles-obj": "^3.0.0"
      },
      "optionalDependencies": {
        "nice-napi": "^1.0.2"
      }
    },
    "node_modules/pkg-dir": {
      "version": "4.2.0",
      "resolved": "https://registry.npmjs.org/pkg-dir/-/pkg-dir-4.2.0.tgz",
      "integrity": "sha512-HRDzbaKjC+AOWVXxAU/x54COGeIv9eb+6CkDSQoNTt4XyWoIJvuPsXizxu/Fr23EiekbtZwmh1IcIG/l/a10GQ==",
      "dev": true,
      "dependencies": {
        "find-up": "^4.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/please-upgrade-node": {
      "version": "3.2.0",
      "resolved": "https://registry.npmjs.org/please-upgrade-node/-/please-upgrade-node-3.2.0.tgz",
      "integrity": "sha512-gQR3WpIgNIKwBMVLkpMUeR3e1/E1y42bqDQZfql+kDeXd8COYfM8PQA4X6y7a8u9Ua9FHmsrrmirW2vHs45hWg==",
      "dependencies": {
        "semver-compare": "^1.0.0"
      }
    },
    "node_modules/pluralize": {
      "version": "8.0.0",
      "resolved": "https://registry.npmjs.org/pluralize/-/pluralize-8.0.0.tgz",
      "integrity": "sha512-Nc3IT5yHzflTfbjgqWcCPpo7DaKy4FnpB0l/zCAW0Tc7jxAiuqSxHasntB3D7887LSrA93kDJ9IXovxJYxyLCA==",
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/portfinder": {
      "version": "1.0.28",
      "resolved": "https://registry.npmjs.org/portfinder/-/portfinder-1.0.28.tgz",
      "integrity": "sha512-Se+2isanIcEqf2XMHjyUKskczxbPH7dQnlMjXX6+dybayyHvAf/TCgyMRlzf/B6QDhAEFOGes0pzRo3by4AbMA==",
      "dev": true,
      "dependencies": {
        "async": "^2.6.2",
        "debug": "^3.1.1",
        "mkdirp": "^0.5.5"
      },
      "engines": {
        "node": ">= 0.12.0"
      }
    },
    "node_modules/portfinder/node_modules/debug": {
      "version": "3.2.7",
      "resolved": "https://registry.npmjs.org/debug/-/debug-3.2.7.tgz",
      "integrity": "sha512-CFjzYYAi4ThfiQvizrFQevTTXHtnCqWfe7x1AhgEscTz6ZbLbfoLRLPugTQyBth6f8ZERVUSyWHFD/7Wu4t1XQ==",
      "dev": true,
      "dependencies": {
        "ms": "^2.1.1"
      }
    },
    "node_modules/portfinder/node_modules/mkdirp": {
      "version": "0.5.5",
      "resolved": "https://registry.npmjs.org/mkdirp/-/mkdirp-0.5.5.tgz",
      "integrity": "sha512-NKmAlESf6jMGym1++R0Ra7wvhV+wFW63FaSOFPwRahvea0gMUcGUhVeAg/0BC0wiv9ih5NYPB1Wn1UEI1/L+xQ==",
      "dev": true,
      "dependencies": {
        "minimist": "^1.2.5"
      },
      "bin": {
        "mkdirp": "bin/cmd.js"
      }
    },
    "node_modules/postcss": {
      "version": "8.4.4",
      "resolved": "https://registry.npmjs.org/postcss/-/postcss-8.4.4.tgz",
      "integrity": "sha512-joU6fBsN6EIer28Lj6GDFoC/5yOZzLCfn0zHAn/MYXI7aPt4m4hK5KC5ovEZXy+lnCjmYIbQWngvju2ddyEr8Q==",
      "dev": true,
      "dependencies": {
        "nanoid": "^3.1.30",
        "picocolors": "^1.0.0",
        "source-map-js": "^1.0.1"
      },
      "engines": {
        "node": "^10 || ^12 || >=14"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/postcss/"
      }
    },
    "node_modules/postcss-attribute-case-insensitive": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/postcss-attribute-case-insensitive/-/postcss-attribute-case-insensitive-5.0.0.tgz",
      "integrity": "sha512-b4g9eagFGq9T5SWX4+USfVyjIb3liPnjhHHRMP7FMB2kFVpYyfEscV0wP3eaXhKlcHKUut8lt5BGoeylWA/dBQ==",
      "dev": true,
      "dependencies": {
        "postcss-selector-parser": "^6.0.2"
      },
      "peerDependencies": {
        "postcss": "^8.0.2"
      }
    },
    "node_modules/postcss-color-functional-notation": {
      "version": "4.2.1",
      "resolved": "https://registry.npmjs.org/postcss-color-functional-notation/-/postcss-color-functional-notation-4.2.1.tgz",
      "integrity": "sha512-62OBIXCjRXpQZcFOYIXwXBlpAVWrYk8ek1rcjvMING4Q2cf0ipyN9qT+BhHA6HmftGSEnFQu2qgKO3gMscl3Rw==",
      "dev": true,
      "dependencies": {
        "postcss-value-parser": "^4.2.0"
      },
      "engines": {
        "node": "^12 || ^14 || >=16"
      },
      "peerDependencies": {
        "postcss": "^8.3"
      }
    },
    "node_modules/postcss-color-hex-alpha": {
      "version": "8.0.2",
      "resolved": "https://registry.npmjs.org/postcss-color-hex-alpha/-/postcss-color-hex-alpha-8.0.2.tgz",
      "integrity": "sha512-gyx8RgqSmGVK156NAdKcsfkY3KPGHhKqvHTL3hhveFrBBToguKFzhyiuk3cljH6L4fJ0Kv+JENuPXs1Wij27Zw==",
      "dev": true,
      "dependencies": {
        "postcss-value-parser": "^4.2.0"
      },
      "engines": {
        "node": "^12 || ^14 || >=16"
      },
      "peerDependencies": {
        "postcss": "^8.3"
      }
    },
    "node_modules/postcss-color-rebeccapurple": {
      "version": "7.0.2",
      "resolved": "https://registry.npmjs.org/postcss-color-rebeccapurple/-/postcss-color-rebeccapurple-7.0.2.tgz",
      "integrity": "sha512-SFc3MaocHaQ6k3oZaFwH8io6MdypkUtEy/eXzXEB1vEQlO3S3oDc/FSZA8AsS04Z25RirQhlDlHLh3dn7XewWw==",
      "dev": true,
      "dependencies": {
        "postcss-value-parser": "^4.2.0"
      },
      "engines": {
        "node": "^12 || ^14 || >=16"
      },
      "peerDependencies": {
        "postcss": "^8.3"
      }
    },
    "node_modules/postcss-custom-media": {
      "version": "8.0.0",
      "resolved": "https://registry.npmjs.org/postcss-custom-media/-/postcss-custom-media-8.0.0.tgz",
      "integrity": "sha512-FvO2GzMUaTN0t1fBULDeIvxr5IvbDXcIatt6pnJghc736nqNgsGao5NT+5+WVLAQiTt6Cb3YUms0jiPaXhL//g==",
      "dev": true,
      "engines": {
        "node": ">=10.0.0"
      },
      "peerDependencies": {
        "postcss": "^8.1.0"
      }
    },
    "node_modules/postcss-custom-properties": {
      "version": "12.1.3",
      "resolved": "https://registry.npmjs.org/postcss-custom-properties/-/postcss-custom-properties-12.1.3.tgz",
      "integrity": "sha512-rtu3otIeY532PnEuuBrIIe+N+pcdbX/7JMZfrcL09wc78YayrHw5E8UkDfvnlOhEUrI4ptCuzXQfj+Or6spbGA==",
      "dev": true,
      "dependencies": {
        "postcss-value-parser": "^4.2.0"
      },
      "engines": {
        "node": "^12 || ^14 || >=16"
      },
      "peerDependencies": {
        "postcss": "^8.3"
      }
    },
    "node_modules/postcss-custom-selectors": {
      "version": "6.0.0",
      "resolved": "https://registry.npmjs.org/postcss-custom-selectors/-/postcss-custom-selectors-6.0.0.tgz",
      "integrity": "sha512-/1iyBhz/W8jUepjGyu7V1OPcGbc636snN1yXEQCinb6Bwt7KxsiU7/bLQlp8GwAXzCh7cobBU5odNn/2zQWR8Q==",
      "dev": true,
      "dependencies": {
        "postcss-selector-parser": "^6.0.4"
      },
      "engines": {
        "node": ">=10.0.0"
      },
      "peerDependencies": {
        "postcss": "^8.1.2"
      }
    },
    "node_modules/postcss-dir-pseudo-class": {
      "version": "6.0.3",
      "resolved": "https://registry.npmjs.org/postcss-dir-pseudo-class/-/postcss-dir-pseudo-class-6.0.3.tgz",
      "integrity": "sha512-qiPm+CNAlgXiMf0J5IbBBEXA9l/Q5HGsNGkL3znIwT2ZFRLGY9U2fTUpa4lqCUXQOxaLimpacHeQC80BD2qbDw==",
      "dev": true,
      "dependencies": {
        "postcss-selector-parser": "^6.0.8"
      },
      "engines": {
        "node": "^12 || ^14 || >=16"
      },
      "peerDependencies": {
        "postcss": "^8.3"
      }
    },
    "node_modules/postcss-double-position-gradients": {
      "version": "3.0.4",
      "resolved": "https://registry.npmjs.org/postcss-double-position-gradients/-/postcss-double-position-gradients-3.0.4.tgz",
      "integrity": "sha512-qz+s5vhKJlsHw8HjSs+HVk2QGFdRyC68KGRQGX3i+GcnUjhWhXQEmCXW6siOJkZ1giu0ddPwSO6I6JdVVVPoog==",
      "dev": true,
      "dependencies": {
        "postcss-value-parser": "^4.2.0"
      },
      "engines": {
        "node": "^12 || ^14 || >=16"
      },
      "peerDependencies": {
        "postcss": "^8.3"
      }
    },
    "node_modules/postcss-env-function": {
      "version": "4.0.4",
      "resolved": "https://registry.npmjs.org/postcss-env-function/-/postcss-env-function-4.0.4.tgz",
      "integrity": "sha512-0ltahRTPtXSIlEZFv7zIvdEib7HN0ZbUQxrxIKn8KbiRyhALo854I/CggU5lyZe6ZBvSTJ6Al2vkZecI2OhneQ==",
      "dev": true,
      "dependencies": {
        "postcss-value-parser": "^4.2.0"
      },
      "engines": {
        "node": "^12 || ^14 || >=16"
      },
      "peerDependencies": {
        "postcss": "^8.3"
      }
    },
    "node_modules/postcss-focus-visible": {
      "version": "6.0.3",
      "resolved": "https://registry.npmjs.org/postcss-focus-visible/-/postcss-focus-visible-6.0.3.tgz",
      "integrity": "sha512-ozOsg+L1U8S+rxSHnJJiET6dNLyADcPHhEarhhtCI9DBLGOPG/2i4ddVoFch9LzrBgb8uDaaRI4nuid2OM82ZA==",
      "dev": true,
      "dependencies": {
        "postcss-selector-parser": "^6.0.8"
      },
      "engines": {
        "node": "^12 || ^14 || >=16"
      },
      "peerDependencies": {
        "postcss": "^8.3"
      }
    },
    "node_modules/postcss-focus-within": {
      "version": "5.0.3",
      "resolved": "https://registry.npmjs.org/postcss-focus-within/-/postcss-focus-within-5.0.3.tgz",
      "integrity": "sha512-fk9y2uFS6/Kpp7/A9Hz9Z4rlFQ8+tzgBcQCXAFSrXFGAbKx+4ZZOmmfHuYjCOMegPWoz0pnC6fNzi8j7Xyqp5Q==",
      "dev": true,
      "dependencies": {
        "postcss-selector-parser": "^6.0.8"
      },
      "engines": {
        "node": "^12 || ^14 || >=16"
      },
      "peerDependencies": {
        "postcss": "^8.3"
      }
    },
    "node_modules/postcss-font-variant": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/postcss-font-variant/-/postcss-font-variant-5.0.0.tgz",
      "integrity": "sha512-1fmkBaCALD72CK2a9i468mA/+tr9/1cBxRRMXOUaZqO43oWPR5imcyPjXwuv7PXbCid4ndlP5zWhidQVVa3hmA==",
      "dev": true,
      "peerDependencies": {
        "postcss": "^8.1.0"
      }
    },
    "node_modules/postcss-gap-properties": {
      "version": "3.0.2",
      "resolved": "https://registry.npmjs.org/postcss-gap-properties/-/postcss-gap-properties-3.0.2.tgz",
      "integrity": "sha512-EaMy/pbxtQnKDsnbEjdqlkCkROTQZzolcLKgIE+3b7EuJfJydH55cZeHfm+MtIezXRqhR80VKgaztO/vHq94Fw==",
      "dev": true,
      "engines": {
        "node": "^12 || ^14 || >=16"
      },
      "peerDependencies": {
        "postcss": "^8.3"
      }
    },
    "node_modules/postcss-image-set-function": {
      "version": "4.0.4",
      "resolved": "https://registry.npmjs.org/postcss-image-set-function/-/postcss-image-set-function-4.0.4.tgz",
      "integrity": "sha512-BlEo9gSTj66lXjRNByvkMK9dEdEGFXRfGjKRi9fo8s0/P3oEk74cAoonl/utiM50E2OPVb/XSu+lWvdW4KtE/Q==",
      "dev": true,
      "dependencies": {
        "postcss-value-parser": "^4.2.0"
      },
      "engines": {
        "node": "^12 || ^14 || >=16"
      },
      "peerDependencies": {
        "postcss": "^8.3"
      }
    },
    "node_modules/postcss-import": {
      "version": "14.0.2",
      "resolved": "https://registry.npmjs.org/postcss-import/-/postcss-import-14.0.2.tgz",
      "integrity": "sha512-BJ2pVK4KhUyMcqjuKs9RijV5tatNzNa73e/32aBVE/ejYPe37iH+6vAu9WvqUkB5OAYgLHzbSvzHnorybJCm9g==",
      "dev": true,
      "dependencies": {
        "postcss-value-parser": "^4.0.0",
        "read-cache": "^1.0.0",
        "resolve": "^1.1.7"
      },
      "engines": {
        "node": ">=10.0.0"
      },
      "peerDependencies": {
        "postcss": "^8.0.0"
      }
    },
    "node_modules/postcss-initial": {
      "version": "4.0.1",
      "resolved": "https://registry.npmjs.org/postcss-initial/-/postcss-initial-4.0.1.tgz",
      "integrity": "sha512-0ueD7rPqX8Pn1xJIjay0AZeIuDoF+V+VvMt/uOnn+4ezUKhZM/NokDeP6DwMNyIoYByuN/94IQnt5FEkaN59xQ==",
      "dev": true,
      "peerDependencies": {
        "postcss": "^8.0.0"
      }
    },
    "node_modules/postcss-lab-function": {
      "version": "4.0.3",
      "resolved": "https://registry.npmjs.org/postcss-lab-function/-/postcss-lab-function-4.0.3.tgz",
      "integrity": "sha512-MH4tymWmefdZQ7uVG/4icfLjAQmH6o2NRYyVh2mKoB4RXJp9PjsyhZwhH4ouaCQHvg+qJVj3RzeAR1EQpIlXZA==",
      "dev": true,
      "dependencies": {
        "postcss-value-parser": "^4.2.0"
      },
      "engines": {
        "node": "^12 || ^14 || >=16"
      },
      "peerDependencies": {
        "postcss": "^8.3"
      }
    },
    "node_modules/postcss-loader": {
      "version": "6.2.1",
      "resolved": "https://registry.npmjs.org/postcss-loader/-/postcss-loader-6.2.1.tgz",
      "integrity": "sha512-WbbYpmAaKcux/P66bZ40bpWsBucjx/TTgVVzRZ9yUO8yQfVBlameJ0ZGVaPfH64hNSBh63a+ICP5nqOpBA0w+Q==",
      "dev": true,
      "dependencies": {
        "cosmiconfig": "^7.0.0",
        "klona": "^2.0.5",
        "semver": "^7.3.5"
      },
      "engines": {
        "node": ">= 12.13.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/webpack"
      },
      "peerDependencies": {
        "postcss": "^7.0.0 || ^8.0.1",
        "webpack": "^5.0.0"
      }
    },
    "node_modules/postcss-logical": {
      "version": "5.0.3",
      "resolved": "https://registry.npmjs.org/postcss-logical/-/postcss-logical-5.0.3.tgz",
      "integrity": "sha512-P5NcHWYrif0vK8rgOy/T87vg0WRIj3HSknrvp1wzDbiBeoDPVmiVRmkown2eSQdpPveat/MC1ess5uhzZFVnqQ==",
      "dev": true,
      "engines": {
        "node": "^12 || ^14 || >=16"
      },
      "peerDependencies": {
        "postcss": "^8.3"
      }
    },
    "node_modules/postcss-media-minmax": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/postcss-media-minmax/-/postcss-media-minmax-5.0.0.tgz",
      "integrity": "sha512-yDUvFf9QdFZTuCUg0g0uNSHVlJ5X1lSzDZjPSFaiCWvjgsvu8vEVxtahPrLMinIDEEGnx6cBe6iqdx5YWz08wQ==",
      "dev": true,
      "engines": {
        "node": ">=10.0.0"
      },
      "peerDependencies": {
        "postcss": "^8.1.0"
      }
    },
    "node_modules/postcss-modules-extract-imports": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/postcss-modules-extract-imports/-/postcss-modules-extract-imports-3.0.0.tgz",
      "integrity": "sha512-bdHleFnP3kZ4NYDhuGlVK+CMrQ/pqUm8bx/oGL93K6gVwiclvX5x0n76fYMKuIGKzlABOy13zsvqjb0f92TEXw==",
      "dev": true,
      "engines": {
        "node": "^10 || ^12 || >= 14"
      },
      "peerDependencies": {
        "postcss": "^8.1.0"
      }
    },
    "node_modules/postcss-modules-local-by-default": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/postcss-modules-local-by-default/-/postcss-modules-local-by-default-4.0.0.tgz",
      "integrity": "sha512-sT7ihtmGSF9yhm6ggikHdV0hlziDTX7oFoXtuVWeDd3hHObNkcHRo9V3yg7vCAY7cONyxJC/XXCmmiHHcvX7bQ==",
      "dev": true,
      "dependencies": {
        "icss-utils": "^5.0.0",
        "postcss-selector-parser": "^6.0.2",
        "postcss-value-parser": "^4.1.0"
      },
      "engines": {
        "node": "^10 || ^12 || >= 14"
      },
      "peerDependencies": {
        "postcss": "^8.1.0"
      }
    },
    "node_modules/postcss-modules-scope": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/postcss-modules-scope/-/postcss-modules-scope-3.0.0.tgz",
      "integrity": "sha512-hncihwFA2yPath8oZ15PZqvWGkWf+XUfQgUGamS4LqoP1anQLOsOJw0vr7J7IwLpoY9fatA2qiGUGmuZL0Iqlg==",
      "dev": true,
      "dependencies": {
        "postcss-selector-parser": "^6.0.4"
      },
      "engines": {
        "node": "^10 || ^12 || >= 14"
      },
      "peerDependencies": {
        "postcss": "^8.1.0"
      }
    },
    "node_modules/postcss-modules-values": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/postcss-modules-values/-/postcss-modules-values-4.0.0.tgz",
      "integrity": "sha512-RDxHkAiEGI78gS2ofyvCsu7iycRv7oqw5xMWn9iMoR0N/7mf9D50ecQqUo5BZ9Zh2vH4bCUR/ktCqbB9m8vJjQ==",
      "dev": true,
      "dependencies": {
        "icss-utils": "^5.0.0"
      },
      "engines": {
        "node": "^10 || ^12 || >= 14"
      },
      "peerDependencies": {
        "postcss": "^8.1.0"
      }
    },
    "node_modules/postcss-nesting": {
      "version": "10.1.2",
      "resolved": "https://registry.npmjs.org/postcss-nesting/-/postcss-nesting-10.1.2.tgz",
      "integrity": "sha512-dJGmgmsvpzKoVMtDMQQG/T6FSqs6kDtUDirIfl4KnjMCiY9/ETX8jdKyCd20swSRAbUYkaBKV20pxkzxoOXLqQ==",
      "dev": true,
      "dependencies": {
        "postcss-selector-parser": "^6.0.8"
      },
      "engines": {
        "node": "^12 || ^14 || >=16"
      },
      "peerDependencies": {
        "postcss": "^8.3"
      }
    },
    "node_modules/postcss-overflow-shorthand": {
      "version": "3.0.2",
      "resolved": "https://registry.npmjs.org/postcss-overflow-shorthand/-/postcss-overflow-shorthand-3.0.2.tgz",
      "integrity": "sha512-odBMVt6PTX7jOE9UNvmnLrFzA9pXS44Jd5shFGGtSHY80QCuJF+14McSy0iavZggRZ9Oj//C9vOKQmexvyEJMg==",
      "dev": true,
      "engines": {
        "node": "^12 || ^14 || >=16"
      },
      "peerDependencies": {
        "postcss": "^8.3"
      }
    },
    "node_modules/postcss-page-break": {
      "version": "3.0.4",
      "resolved": "https://registry.npmjs.org/postcss-page-break/-/postcss-page-break-3.0.4.tgz",
      "integrity": "sha512-1JGu8oCjVXLa9q9rFTo4MbeeA5FMe00/9C7lN4va606Rdb+HkxXtXsmEDrIraQ11fGz/WvKWa8gMuCKkrXpTsQ==",
      "dev": true,
      "peerDependencies": {
        "postcss": "^8"
      }
    },
    "node_modules/postcss-place": {
      "version": "7.0.3",
      "resolved": "https://registry.npmjs.org/postcss-place/-/postcss-place-7.0.3.tgz",
      "integrity": "sha512-tDQ3m+GYoOar+KoQgj+pwPAvGHAp/Sby6vrFiyrELrMKQJ4AejL0NcS0mm296OKKYA2SRg9ism/hlT/OLhBrdQ==",
      "dev": true,
      "dependencies": {
        "postcss-value-parser": "^4.2.0"
      },
      "engines": {
        "node": "^12 || ^14 || >=16"
      },
      "peerDependencies": {
        "postcss": "^8.3"
      }
    },
    "node_modules/postcss-preset-env": {
      "version": "7.2.3",
      "resolved": "https://registry.npmjs.org/postcss-preset-env/-/postcss-preset-env-7.2.3.tgz",
      "integrity": "sha512-Ok0DhLfwrcNGrBn8sNdy1uZqWRk/9FId0GiQ39W4ILop5GHtjJs8bu1MY9isPwHInpVEPWjb4CEcEaSbBLpfwA==",
      "dev": true,
      "dependencies": {
        "autoprefixer": "^10.4.2",
        "browserslist": "^4.19.1",
        "caniuse-lite": "^1.0.30001299",
        "css-blank-pseudo": "^3.0.2",
        "css-has-pseudo": "^3.0.3",
        "css-prefers-color-scheme": "^6.0.2",
        "cssdb": "^5.0.0",
        "postcss-attribute-case-insensitive": "^5.0.0",
        "postcss-color-functional-notation": "^4.2.1",
        "postcss-color-hex-alpha": "^8.0.2",
        "postcss-color-rebeccapurple": "^7.0.2",
        "postcss-custom-media": "^8.0.0",
        "postcss-custom-properties": "^12.1.2",
        "postcss-custom-selectors": "^6.0.0",
        "postcss-dir-pseudo-class": "^6.0.3",
        "postcss-double-position-gradients": "^3.0.4",
        "postcss-env-function": "^4.0.4",
        "postcss-focus-visible": "^6.0.3",
        "postcss-focus-within": "^5.0.3",
        "postcss-font-variant": "^5.0.0",
        "postcss-gap-properties": "^3.0.2",
        "postcss-image-set-function": "^4.0.4",
        "postcss-initial": "^4.0.1",
        "postcss-lab-function": "^4.0.3",
        "postcss-logical": "^5.0.3",
        "postcss-media-minmax": "^5.0.0",
        "postcss-nesting": "^10.1.2",
        "postcss-overflow-shorthand": "^3.0.2",
        "postcss-page-break": "^3.0.4",
        "postcss-place": "^7.0.3",
        "postcss-pseudo-class-any-link": "^7.0.2",
        "postcss-replace-overflow-wrap": "^4.0.0",
        "postcss-selector-not": "^5.0.0"
      },
      "engines": {
        "node": "^12 || ^14 || >=16"
      },
      "peerDependencies": {
        "postcss": "^8.4"
      }
    },
    "node_modules/postcss-pseudo-class-any-link": {
      "version": "7.0.2",
      "resolved": "https://registry.npmjs.org/postcss-pseudo-class-any-link/-/postcss-pseudo-class-any-link-7.0.2.tgz",
      "integrity": "sha512-CG35J1COUH7OOBgpw5O+0koOLUd5N4vUGKUqSAuIe4GiuLHWU96Pqp+UPC8QITTd12zYAFx76pV7qWT/0Aj/TA==",
      "dev": true,
      "dependencies": {
        "postcss-selector-parser": "^6.0.8"
      },
      "engines": {
        "node": "^12 || ^14 || >=16"
      },
      "peerDependencies": {
        "postcss": "^8.3"
      }
    },
    "node_modules/postcss-replace-overflow-wrap": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/postcss-replace-overflow-wrap/-/postcss-replace-overflow-wrap-4.0.0.tgz",
      "integrity": "sha512-KmF7SBPphT4gPPcKZc7aDkweHiKEEO8cla/GjcBK+ckKxiZslIu3C4GCRW3DNfL0o7yW7kMQu9xlZ1kXRXLXtw==",
      "dev": true,
      "peerDependencies": {
        "postcss": "^8.0.3"
      }
    },
    "node_modules/postcss-selector-not": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/postcss-selector-not/-/postcss-selector-not-5.0.0.tgz",
      "integrity": "sha512-/2K3A4TCP9orP4TNS7u3tGdRFVKqz/E6pX3aGnriPG0jU78of8wsUcqE4QAhWEU0d+WnMSF93Ah3F//vUtK+iQ==",
      "dev": true,
      "dependencies": {
        "balanced-match": "^1.0.0"
      },
      "peerDependencies": {
        "postcss": "^8.1.0"
      }
    },
    "node_modules/postcss-selector-parser": {
      "version": "6.0.9",
      "resolved": "https://registry.npmjs.org/postcss-selector-parser/-/postcss-selector-parser-6.0.9.tgz",
      "integrity": "sha512-UO3SgnZOVTwu4kyLR22UQ1xZh086RyNZppb7lLAKBFK8a32ttG5i87Y/P3+2bRSjZNyJ1B7hfFNo273tKe9YxQ==",
      "dev": true,
      "dependencies": {
        "cssesc": "^3.0.0",
        "util-deprecate": "^1.0.2"
      },
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/postcss-value-parser": {
      "version": "4.2.0",
      "resolved": "https://registry.npmjs.org/postcss-value-parser/-/postcss-value-parser-4.2.0.tgz",
      "integrity": "sha512-1NNCs6uurfkVbeXG4S8JFT9t19m45ICnif8zWLd5oPSZ50QnwMfK+H3jv408d4jw/7Bttv5axS5IiHoLaVNHeQ==",
      "dev": true
    },
    "node_modules/prepend-http": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/prepend-http/-/prepend-http-2.0.0.tgz",
      "integrity": "sha1-6SQ0v6XqjBn0HN/UAddBo8gZ2Jc=",
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/pretty-bytes": {
      "version": "5.6.0",
      "resolved": "https://registry.npmjs.org/pretty-bytes/-/pretty-bytes-5.6.0.tgz",
      "integrity": "sha512-FFw039TmrBqFK8ma/7OL3sDz/VytdtJr044/QUJtH0wK9lb9jLq9tJyIxUwtQJHwar2BqtiA4iCWSwo9JLkzFg==",
      "dev": true,
      "engines": {
        "node": ">=6"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/process-nextick-args": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/process-nextick-args/-/process-nextick-args-2.0.1.tgz",
      "integrity": "sha512-3ouUOpQhtgrbOa17J7+uxOTpITYWaGP7/AhoR3+A+/1e9skrzelGi/dXzEYyvbxubEF6Wn2ypscTKiKJFFn1ag==",
      "dev": true
    },
    "node_modules/promise-inflight": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/promise-inflight/-/promise-inflight-1.0.1.tgz",
      "integrity": "sha1-mEcocL8igTL8vdhoEputEsPAKeM=",
      "dev": true
    },
    "node_modules/promise-retry": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/promise-retry/-/promise-retry-2.0.1.tgz",
      "integrity": "sha512-y+WKFlBR8BGXnsNlIHFGPZmyDf3DFMoLhaflAnyZgV6rG6xu+JwesTo2Q9R6XwYmtmwAFCkAk3e35jEdoeh/3g==",
      "dev": true,
      "dependencies": {
        "err-code": "^2.0.2",
        "retry": "^0.12.0"
      },
      "engines": {
        "node": ">=10"
      }
    },
    "node_modules/proxy-addr": {
      "version": "2.0.7",
      "resolved": "https://registry.npmjs.org/proxy-addr/-/proxy-addr-2.0.7.tgz",
      "integrity": "sha512-llQsMLSUDUPT44jdrU/O37qlnifitDP+ZwrmmZcoSKyLKvtZxpyV0n2/bD/N4tBAAZ/gJEdZU7KMraoK1+XYAg==",
      "dependencies": {
        "forwarded": "0.2.0",
        "ipaddr.js": "1.9.1"
      },
      "engines": {
        "node": ">= 0.10"
      }
    },
    "node_modules/proxy-addr/node_modules/ipaddr.js": {
      "version": "1.9.1",
      "resolved": "https://registry.npmjs.org/ipaddr.js/-/ipaddr.js-1.9.1.tgz",
      "integrity": "sha512-0KI/607xoxSToH7GjN1FfSbLoU0+btTicjsQSWQlh/hZykN8KpmMf7uYwPW3R+akZ6R/w18ZlXSHBYXiYUPO3g==",
      "engines": {
        "node": ">= 0.10"
      }
    },
    "node_modules/prr": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/prr/-/prr-1.0.1.tgz",
      "integrity": "sha1-0/wRS6BplaRexok/SEzrHXj19HY=",
      "dev": true,
      "optional": true
    },
    "node_modules/pump": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/pump/-/pump-3.0.0.tgz",
      "integrity": "sha512-LwZy+p3SFs1Pytd/jYct4wpv49HiYCqd9Rlc5ZVdk0V+8Yzv6jR5Blk3TRmPL1ft69TxP0IMZGJ+WPFU2BFhww==",
      "dependencies": {
        "end-of-stream": "^1.1.0",
        "once": "^1.3.1"
      }
    },
    "node_modules/punycode": {
      "version": "2.1.1",
      "resolved": "https://registry.npmjs.org/punycode/-/punycode-2.1.1.tgz",
      "integrity": "sha512-XRsRjdf+j5ml+y/6GKHPZbrF/8p2Yga0JPtdqTIY2Xe5ohJPD9saDJJLPvp9+NSBprVvevdXZybnj2cv8OEd0A==",
      "dev": true,
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/pupa": {
      "version": "2.1.1",
      "resolved": "https://registry.npmjs.org/pupa/-/pupa-2.1.1.tgz",
      "integrity": "sha512-l1jNAspIBSFqbT+y+5FosojNpVpF94nlI+wDUpqP9enwOTfHx9f0gh5nB96vl+6yTpsJsypeNrwfzPrKuHB41A==",
      "dependencies": {
        "escape-goat": "^2.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/qjobs": {
      "version": "1.2.0",
      "resolved": "https://registry.npmjs.org/qjobs/-/qjobs-1.2.0.tgz",
      "integrity": "sha512-8YOJEHtxpySA3fFDyCRxA+UUV+fA+rTWnuWvylOK/NCjhY+b4ocCtmu8TtsWb+mYeU+GCHf/S66KZF/AsteKHg==",
      "dev": true,
      "engines": {
        "node": ">=0.9"
      }
    },
    "node_modules/qs": {
      "version": "6.9.6",
      "resolved": "https://registry.npmjs.org/qs/-/qs-6.9.6.tgz",
      "integrity": "sha512-TIRk4aqYLNoJUbd+g2lEdz5kLWIuTMRagAXxl78Q0RiVjAOugHmeKNGdd3cwo/ktpf9aL9epCfFqWDEKysUlLQ==",
      "engines": {
        "node": ">=0.6"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/querystring": {
      "version": "0.2.0",
      "resolved": "https://registry.npmjs.org/querystring/-/querystring-0.2.0.tgz",
      "integrity": "sha1-sgmEkgO7Jd+CDadW50cAWHhSFiA=",
      "deprecated": "The querystring API is considered Legacy. new code should use the URLSearchParams API instead.",
      "dev": true,
      "engines": {
        "node": ">=0.4.x"
      }
    },
    "node_modules/queue-microtask": {
      "version": "1.2.3",
      "resolved": "https://registry.npmjs.org/queue-microtask/-/queue-microtask-1.2.3.tgz",
      "integrity": "sha512-NuaNSa6flKT5JaSYQzJok04JzTL1CA6aGhv5rfLW3PgqA+M2ChpZQnAC8h8i4ZFkBS8X5RqkDBHA7r4hej3K9A==",
      "dev": true,
      "funding": [
        {
          "type": "github",
          "url": "https://github.com/sponsors/feross"
        },
        {
          "type": "patreon",
          "url": "https://www.patreon.com/feross"
        },
        {
          "type": "consulting",
          "url": "https://feross.org/support"
        }
      ]
    },
    "node_modules/randombytes": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/randombytes/-/randombytes-2.1.0.tgz",
      "integrity": "sha512-vYl3iOX+4CKUWuxGi9Ukhie6fsqXqS9FE2Zaic4tNFD2N2QQaXOMFbuKK4QmDHC0JO6B1Zp41J0LpT0oR68amQ==",
      "dev": true,
      "dependencies": {
        "safe-buffer": "^5.1.0"
      }
    },
    "node_modules/range-parser": {
      "version": "1.2.1",
      "resolved": "https://registry.npmjs.org/range-parser/-/range-parser-1.2.1.tgz",
      "integrity": "sha512-Hrgsx+orqoygnmhFbKaHE6c296J+HTAQXoxEF6gNupROmmGJRoyzfG3ccAveqCBrwr/2yxQ5BVd/GTl5agOwSg==",
      "engines": {
        "node": ">= 0.6"
      }
    },
    "node_modules/raw-body": {
      "version": "2.4.2",
      "resolved": "https://registry.npmjs.org/raw-body/-/raw-body-2.4.2.tgz",
      "integrity": "sha512-RPMAFUJP19WIet/99ngh6Iv8fzAbqum4Li7AD6DtGaW2RpMB/11xDoalPiJMTbu6I3hkbMVkATvZrqb9EEqeeQ==",
      "dependencies": {
        "bytes": "3.1.1",
        "http-errors": "1.8.1",
        "iconv-lite": "0.4.24",
        "unpipe": "1.0.0"
      },
      "engines": {
        "node": ">= 0.8"
      }
    },
    "node_modules/rc": {
      "version": "1.2.8",
      "resolved": "https://registry.npmjs.org/rc/-/rc-1.2.8.tgz",
      "integrity": "sha512-y3bGgqKj3QBdxLbLkomlohkvsA8gdAiUQlSBJnBhfn+BPxg4bc62d8TcBW15wavDfgexCgccckhcZvywyQYPOw==",
      "dependencies": {
        "deep-extend": "^0.6.0",
        "ini": "~1.3.0",
        "minimist": "^1.2.0",
        "strip-json-comments": "~2.0.1"
      },
      "bin": {
        "rc": "cli.js"
      }
    },
    "node_modules/rc/node_modules/ini": {
      "version": "1.3.8",
      "resolved": "https://registry.npmjs.org/ini/-/ini-1.3.8.tgz",
      "integrity": "sha512-JV/yugV2uzW5iMRSiZAyDtQd+nxtUnjeLt0acNdw98kKLrvuRVyB80tsREOE7yvGVgalhZ6RNXCmEHkUKBKxew=="
    },
    "node_modules/read-cache": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/read-cache/-/read-cache-1.0.0.tgz",
      "integrity": "sha1-5mTvMRYRZsl1HNvo28+GtftY93Q=",
      "dev": true,
      "dependencies": {
        "pify": "^2.3.0"
      }
    },
    "node_modules/read-package-json-fast": {
      "version": "2.0.3",
      "resolved": "https://registry.npmjs.org/read-package-json-fast/-/read-package-json-fast-2.0.3.tgz",
      "integrity": "sha512-W/BKtbL+dUjTuRL2vziuYhp76s5HZ9qQhd/dKfWIZveD0O40453QNyZhC0e63lqZrAQ4jiOapVoeJ7JrszenQQ==",
      "dev": true,
      "dependencies": {
        "json-parse-even-better-errors": "^2.3.0",
        "npm-normalize-package-bin": "^1.0.1"
      },
      "engines": {
        "node": ">=10"
      }
    },
    "node_modules/readable-stream": {
      "version": "3.6.0",
      "resolved": "https://registry.npmjs.org/readable-stream/-/readable-stream-3.6.0.tgz",
      "integrity": "sha512-BViHy7LKeTz4oNnkcLJ+lVSL6vpiFeX6/d3oSH8zCW7UxP2onchk+vTGB143xuFjHS3deTgkKoXXymXqymiIdA==",
      "dev": true,
      "dependencies": {
        "inherits": "^2.0.3",
        "string_decoder": "^1.1.1",
        "util-deprecate": "^1.0.1"
      },
      "engines": {
        "node": ">= 6"
      }
    },
    "node_modules/readdirp": {
      "version": "3.6.0",
      "resolved": "https://registry.npmjs.org/readdirp/-/readdirp-3.6.0.tgz",
      "integrity": "sha512-hOS089on8RduqdbhvQ5Z37A0ESjsqz6qnRcffsMU3495FuTdqSm+7bhJ29JvIOsBDEEnan5DPu9t3To9VRlMzA==",
      "dev": true,
      "dependencies": {
        "picomatch": "^2.2.1"
      },
      "engines": {
        "node": ">=8.10.0"
      }
    },
    "node_modules/reflect-metadata": {
      "version": "0.1.13",
      "resolved": "https://registry.npmjs.org/reflect-metadata/-/reflect-metadata-0.1.13.tgz",
      "integrity": "sha512-Ts1Y/anZELhSsjMcU605fU9RE4Oi3p5ORujwbIKXfWa+0Zxs510Qrmrce5/Jowq3cHSZSJqBjypxmHarc+vEWg==",
      "dev": true
    },
    "node_modules/regenerate": {
      "version": "1.4.2",
      "resolved": "https://registry.npmjs.org/regenerate/-/regenerate-1.4.2.tgz",
      "integrity": "sha512-zrceR/XhGYU/d/opr2EKO7aRHUeiBI8qjtfHqADTwZd6Szfy16la6kqD0MIUs5z5hx6AaKa+PixpPrR289+I0A==",
      "dev": true
    },
    "node_modules/regenerate-unicode-properties": {
      "version": "9.0.0",
      "resolved": "https://registry.npmjs.org/regenerate-unicode-properties/-/regenerate-unicode-properties-9.0.0.tgz",
      "integrity": "sha512-3E12UeNSPfjrgwjkR81m5J7Aw/T55Tu7nUyZVQYCKEOs+2dkxEY+DpPtZzO4YruuiPb7NkYLVcyJC4+zCbk5pA==",
      "dev": true,
      "dependencies": {
        "regenerate": "^1.4.2"
      },
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/regenerator-runtime": {
      "version": "0.13.9",
      "resolved": "https://registry.npmjs.org/regenerator-runtime/-/regenerator-runtime-0.13.9.tgz",
      "integrity": "sha512-p3VT+cOEgxFsRRA9X4lkI1E+k2/CtnKtU4gcxyaCUreilL/vqI6CdZ3wxVUx3UOUg+gnUOQQcRI7BmSI656MYA==",
      "dev": true
    },
    "node_modules/regenerator-transform": {
      "version": "0.14.5",
      "resolved": "https://registry.npmjs.org/regenerator-transform/-/regenerator-transform-0.14.5.tgz",
      "integrity": "sha512-eOf6vka5IO151Jfsw2NO9WpGX58W6wWmefK3I1zEGr0lOD0u8rwPaNqQL1aRxUaxLeKO3ArNh3VYg1KbaD+FFw==",
      "dev": true,
      "dependencies": {
        "@babel/runtime": "^7.8.4"
      }
    },
    "node_modules/regex-parser": {
      "version": "2.2.11",
      "resolved": "https://registry.npmjs.org/regex-parser/-/regex-parser-2.2.11.tgz",
      "integrity": "sha512-jbD/FT0+9MBU2XAZluI7w2OBs1RBi6p9M83nkoZayQXXU9e8Robt69FcZc7wU4eJD/YFTjn1JdCk3rbMJajz8Q==",
      "dev": true
    },
    "node_modules/regexp.prototype.flags": {
      "version": "1.4.1",
      "resolved": "https://registry.npmjs.org/regexp.prototype.flags/-/regexp.prototype.flags-1.4.1.tgz",
      "integrity": "sha512-pMR7hBVUUGI7PMA37m2ofIdQCsomVnas+Jn5UPGAHQ+/LlwKm/aTLJHdasmHRzlfeZwHiAOaRSo2rbBDm3nNUQ==",
      "dev": true,
      "dependencies": {
        "call-bind": "^1.0.2",
        "define-properties": "^1.1.3"
      },
      "engines": {
        "node": ">= 0.4"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/regexpu-core": {
      "version": "4.8.0",
      "resolved": "https://registry.npmjs.org/regexpu-core/-/regexpu-core-4.8.0.tgz",
      "integrity": "sha512-1F6bYsoYiz6is+oz70NWur2Vlh9KWtswuRuzJOfeYUrfPX2o8n74AnUVaOGDbUqVGO9fNHu48/pjJO4sNVwsOg==",
      "dev": true,
      "dependencies": {
        "regenerate": "^1.4.2",
        "regenerate-unicode-properties": "^9.0.0",
        "regjsgen": "^0.5.2",
        "regjsparser": "^0.7.0",
        "unicode-match-property-ecmascript": "^2.0.0",
        "unicode-match-property-value-ecmascript": "^2.0.0"
      },
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/registry-auth-token": {
      "version": "4.2.1",
      "resolved": "https://registry.npmjs.org/registry-auth-token/-/registry-auth-token-4.2.1.tgz",
      "integrity": "sha512-6gkSb4U6aWJB4SF2ZvLb76yCBjcvufXBqvvEx1HbmKPkutswjW1xNVRY0+daljIYRbogN7O0etYSlbiaEQyMyw==",
      "dependencies": {
        "rc": "^1.2.8"
      },
      "engines": {
        "node": ">=6.0.0"
      }
    },
    "node_modules/registry-url": {
      "version": "5.1.0",
      "resolved": "https://registry.npmjs.org/registry-url/-/registry-url-5.1.0.tgz",
      "integrity": "sha512-8acYXXTI0AkQv6RAOjE3vOaIXZkT9wo4LOFbBKYQEEnnMNBpKqdUrI6S4NT0KPIo/WVvJ5tE/X5LF/TQUf0ekw==",
      "dependencies": {
        "rc": "^1.2.8"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/regjsgen": {
      "version": "0.5.2",
      "resolved": "https://registry.npmjs.org/regjsgen/-/regjsgen-0.5.2.tgz",
      "integrity": "sha512-OFFT3MfrH90xIW8OOSyUrk6QHD5E9JOTeGodiJeBS3J6IwlgzJMNE/1bZklWz5oTg+9dCMyEetclvCVXOPoN3A==",
      "dev": true
    },
    "node_modules/regjsparser": {
      "version": "0.7.0",
      "resolved": "https://registry.npmjs.org/regjsparser/-/regjsparser-0.7.0.tgz",
      "integrity": "sha512-A4pcaORqmNMDVwUjWoTzuhwMGpP+NykpfqAsEgI1FSH/EzC7lrN5TMd+kN8YCovX+jMpu8eaqXgXPCa0g8FQNQ==",
      "dev": true,
      "dependencies": {
        "jsesc": "~0.5.0"
      },
      "bin": {
        "regjsparser": "bin/parser"
      }
    },
    "node_modules/regjsparser/node_modules/jsesc": {
      "version": "0.5.0",
      "resolved": "https://registry.npmjs.org/jsesc/-/jsesc-0.5.0.tgz",
      "integrity": "sha1-597mbjXW/Bb3EP6R1c9p9w8IkR0=",
      "dev": true,
      "bin": {
        "jsesc": "bin/jsesc"
      }
    },
    "node_modules/require-directory": {
      "version": "2.1.1",
      "resolved": "https://registry.npmjs.org/require-directory/-/require-directory-2.1.1.tgz",
      "integrity": "sha1-jGStX9MNqxyXbiNE/+f3kqam30I=",
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/require-from-string": {
      "version": "2.0.2",
      "resolved": "https://registry.npmjs.org/require-from-string/-/require-from-string-2.0.2.tgz",
      "integrity": "sha512-Xf0nWe6RseziFMu+Ap9biiUbmplq6S9/p+7w7YXP/JBHhrUDDUhwa+vANyubuqfZWTveU//DYVGsDG7RKL/vEw==",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/requires-port": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/requires-port/-/requires-port-1.0.0.tgz",
      "integrity": "sha1-kl0mAdOaxIXgkc8NpcbmlNw9yv8=",
      "dev": true
    },
    "node_modules/resolve": {
      "version": "1.20.0",
      "resolved": "https://registry.npmjs.org/resolve/-/resolve-1.20.0.tgz",
      "integrity": "sha512-wENBPt4ySzg4ybFQW2TT1zMQucPK95HSh/nq2CFTZVOGut2+pQvSsgtda4d26YrYcr067wjbmzOG8byDPBX63A==",
      "dev": true,
      "dependencies": {
        "is-core-module": "^2.2.0",
        "path-parse": "^1.0.6"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/resolve-from": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/resolve-from/-/resolve-from-5.0.0.tgz",
      "integrity": "sha512-qYg9KP24dD5qka9J47d0aVky0N+b4fTU89LN9iDnjB5waksiC49rvMB0PrUJQGoTmH50XPiqOvAjDfaijGxYZw==",
      "dev": true,
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/resolve-url-loader": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/resolve-url-loader/-/resolve-url-loader-4.0.0.tgz",
      "integrity": "sha512-05VEMczVREcbtT7Bz+C+96eUO5HDNvdthIiMB34t7FcF8ehcu4wC0sSgPUubs3XW2Q3CNLJk/BJrCU9wVRymiA==",
      "dev": true,
      "dependencies": {
        "adjust-sourcemap-loader": "^4.0.0",
        "convert-source-map": "^1.7.0",
        "loader-utils": "^2.0.0",
        "postcss": "^7.0.35",
        "source-map": "0.6.1"
      },
      "engines": {
        "node": ">=8.9"
      },
      "peerDependencies": {
        "rework": "1.0.1",
        "rework-visit": "1.0.0"
      },
      "peerDependenciesMeta": {
        "rework": {
          "optional": true
        },
        "rework-visit": {
          "optional": true
        }
      }
    },
    "node_modules/resolve-url-loader/node_modules/loader-utils": {
      "version": "2.0.2",
      "resolved": "https://registry.npmjs.org/loader-utils/-/loader-utils-2.0.2.tgz",
      "integrity": "sha512-TM57VeHptv569d/GKh6TAYdzKblwDNiumOdkFnejjD0XwTH87K90w3O7AiJRqdQoXygvi1VQTJTLGhJl7WqA7A==",
      "dev": true,
      "dependencies": {
        "big.js": "^5.2.2",
        "emojis-list": "^3.0.0",
        "json5": "^2.1.2"
      },
      "engines": {
        "node": ">=8.9.0"
      }
    },
    "node_modules/resolve-url-loader/node_modules/picocolors": {
      "version": "0.2.1",
      "resolved": "https://registry.npmjs.org/picocolors/-/picocolors-0.2.1.tgz",
      "integrity": "sha512-cMlDqaLEqfSaW8Z7N5Jw+lyIW869EzT73/F5lhtY9cLGoVxSXznfgfXMO0Z5K0o0Q2TkTXq+0KFsdnSe3jDViA==",
      "dev": true
    },
    "node_modules/resolve-url-loader/node_modules/postcss": {
      "version": "7.0.39",
      "resolved": "https://registry.npmjs.org/postcss/-/postcss-7.0.39.tgz",
      "integrity": "sha512-yioayjNbHn6z1/Bywyb2Y4s3yvDAeXGOyxqD+LnVOinq6Mdmd++SW2wUNVzavyyHxd6+DxzWGIuosg6P1Rj8uA==",
      "dev": true,
      "dependencies": {
        "picocolors": "^0.2.1",
        "source-map": "^0.6.1"
      },
      "engines": {
        "node": ">=6.0.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/postcss/"
      }
    },
    "node_modules/resolve-url-loader/node_modules/source-map": {
      "version": "0.6.1",
      "resolved": "https://registry.npmjs.org/source-map/-/source-map-0.6.1.tgz",
      "integrity": "sha512-UjgapumWlbMhkBgzT7Ykc5YXUT46F0iKu8SGXq0bcwP5dz/h0Plj6enJqjz1Zbq2l5WaqYnrVbwWOWMyF3F47g==",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/responselike": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/responselike/-/responselike-1.0.2.tgz",
      "integrity": "sha1-kYcg7ztjHFZCvgaPFa3lpG9Loec=",
      "dependencies": {
        "lowercase-keys": "^1.0.0"
      }
    },
    "node_modules/restore-cursor": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/restore-cursor/-/restore-cursor-3.1.0.tgz",
      "integrity": "sha512-l+sSefzHpj5qimhFSE5a8nufZYAM3sBSVMAPtYkmC+4EH2anSGaEMXSD0izRQbu9nfyQ9y5JrVmp7E8oZrUjvA==",
      "dev": true,
      "dependencies": {
        "onetime": "^5.1.0",
        "signal-exit": "^3.0.2"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/retry": {
      "version": "0.12.0",
      "resolved": "https://registry.npmjs.org/retry/-/retry-0.12.0.tgz",
      "integrity": "sha1-G0KmJmoh8HQh0bC1S33BZ7AcATs=",
      "dev": true,
      "engines": {
        "node": ">= 4"
      }
    },
    "node_modules/reusify": {
      "version": "1.0.4",
      "resolved": "https://registry.npmjs.org/reusify/-/reusify-1.0.4.tgz",
      "integrity": "sha512-U9nH88a3fc/ekCF1l0/UP1IosiuIjyTh7hBvXVMHYgVcfGvt897Xguj2UOLDeI5BG2m7/uwyaLVT6fbtCwTyzw==",
      "dev": true,
      "engines": {
        "iojs": ">=1.0.0",
        "node": ">=0.10.0"
      }
    },
    "node_modules/rfdc": {
      "version": "1.3.0",
      "resolved": "https://registry.npmjs.org/rfdc/-/rfdc-1.3.0.tgz",
      "integrity": "sha512-V2hovdzFbOi77/WajaSMXk2OLm+xNIeQdMMuB7icj7bk6zi2F8GGAxigcnDFpJHbNyNcgyJDiP+8nOrY5cZGrA==",
      "dev": true
    },
    "node_modules/rimraf": {
      "version": "3.0.2",
      "resolved": "https://registry.npmjs.org/rimraf/-/rimraf-3.0.2.tgz",
      "integrity": "sha512-JZkJMZkAGFFPP2YqXZXPbMlMBgsxzE8ILs4lMIX/2o0L9UBw9O/Y3o6wFw/i9YLapcUJWwqbi3kdxIPdC62TIA==",
      "dev": true,
      "dependencies": {
        "glob": "^7.1.3"
      },
      "bin": {
        "rimraf": "bin.js"
      },
      "funding": {
        "url": "https://github.com/sponsors/isaacs"
      }
    },
    "node_modules/run-async": {
      "version": "2.4.1",
      "resolved": "https://registry.npmjs.org/run-async/-/run-async-2.4.1.tgz",
      "integrity": "sha512-tvVnVv01b8c1RrA6Ep7JkStj85Guv/YrMcwqYQnwjsAS2cTmmPGBBjAjpCW7RrSodNSoE2/qg9O4bceNvUuDgQ==",
      "dev": true,
      "engines": {
        "node": ">=0.12.0"
      }
    },
    "node_modules/run-parallel": {
      "version": "1.2.0",
      "resolved": "https://registry.npmjs.org/run-parallel/-/run-parallel-1.2.0.tgz",
      "integrity": "sha512-5l4VyZR86LZ/lDxZTR6jqL8AFE2S0IFLMP26AbjsLVADxHdhB/c0GUsH+y39UfCi3dzz8OlQuPmnaJOMoDHQBA==",
      "dev": true,
      "funding": [
        {
          "type": "github",
          "url": "https://github.com/sponsors/feross"
        },
        {
          "type": "patreon",
          "url": "https://www.patreon.com/feross"
        },
        {
          "type": "consulting",
          "url": "https://feross.org/support"
        }
      ],
      "dependencies": {
        "queue-microtask": "^1.2.2"
      }
    },
    "node_modules/rxjs": {
      "version": "7.4.0",
      "resolved": "https://registry.npmjs.org/rxjs/-/rxjs-7.4.0.tgz",
      "integrity": "sha512-7SQDi7xeTMCJpqViXh8gL/lebcwlp3d831F05+9B44A4B0WfsEwUQHR64gsH1kvJ+Ep/J9K2+n1hVl1CsGN23w==",
      "dependencies": {
        "tslib": "~2.1.0"
      }
    },
    "node_modules/rxjs/node_modules/tslib": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.1.0.tgz",
      "integrity": "sha512-hcVC3wYEziELGGmEEXue7D75zbwIIVUMWAVbHItGPx0ziyXxrOMQx4rQEVEV45Ut/1IotuEvwqPopzIOkDMf0A=="
    },
    "node_modules/safe-buffer": {
      "version": "5.1.2",
      "resolved": "https://registry.npmjs.org/safe-buffer/-/safe-buffer-5.1.2.tgz",
      "integrity": "sha512-Gd2UZBJDkXlY7GbJxfsE8/nvKkUEU1G38c1siN6QP6a9PT9MmHB8GnpscSmMJSoF8LOIrt8ud/wPtojys4G6+g=="
    },
    "node_modules/safer-buffer": {
      "version": "2.1.2",
      "resolved": "https://registry.npmjs.org/safer-buffer/-/safer-buffer-2.1.2.tgz",
      "integrity": "sha512-YZo3K82SD7Riyi0E1EQPojLz7kpepnSQI9IyPbHHg1XXXevb5dJI7tpyN2ADxGcQbHG7vcyRHk0cbwqcQriUtg=="
    },
    "node_modules/sass": {
      "version": "1.44.0",
      "resolved": "https://registry.npmjs.org/sass/-/sass-1.44.0.tgz",
      "integrity": "sha512-0hLREbHFXGQqls/K8X+koeP+ogFRPF4ZqetVB19b7Cst9Er8cOR0rc6RU7MaI4W1JmUShd1BPgPoeqmmgMMYFw==",
      "dev": true,
      "dependencies": {
        "chokidar": ">=3.0.0 <4.0.0",
        "immutable": "^4.0.0"
      },
      "bin": {
        "sass": "sass.js"
      },
      "engines": {
        "node": ">=8.9.0"
      }
    },
    "node_modules/sass-loader": {
      "version": "12.4.0",
      "resolved": "https://registry.npmjs.org/sass-loader/-/sass-loader-12.4.0.tgz",
      "integrity": "sha512-7xN+8khDIzym1oL9XyS6zP6Ges+Bo2B2xbPrjdMHEYyV3AQYhd/wXeru++3ODHF0zMjYmVadblSKrPrjEkL8mg==",
      "dev": true,
      "dependencies": {
        "klona": "^2.0.4",
        "neo-async": "^2.6.2"
      },
      "engines": {
        "node": ">= 12.13.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/webpack"
      },
      "peerDependencies": {
        "fibers": ">= 3.1.0",
        "node-sass": "^4.0.0 || ^5.0.0 || ^6.0.0 || ^7.0.0",
        "sass": "^1.3.0",
        "webpack": "^5.0.0"
      },
      "peerDependenciesMeta": {
        "fibers": {
          "optional": true
        },
        "node-sass": {
          "optional": true
        },
        "sass": {
          "optional": true
        }
      }
    },
    "node_modules/sax": {
      "version": "1.2.4",
      "resolved": "https://registry.npmjs.org/sax/-/sax-1.2.4.tgz",
      "integrity": "sha512-NqVDv9TpANUjFm0N8uM5GxL36UgKi9/atZw+x7YFnQ8ckwFGKrl4xX4yWtrey3UJm5nP1kUbnYgLopqWNSRhWw==",
      "dev": true
    },
    "node_modules/schema-utils": {
      "version": "2.7.1",
      "resolved": "https://registry.npmjs.org/schema-utils/-/schema-utils-2.7.1.tgz",
      "integrity": "sha512-SHiNtMOUGWBQJwzISiVYKu82GiV4QYGePp3odlY1tuKO7gPtphAT5R/py0fA6xtbgLL/RvtJZnU9b8s0F1q0Xg==",
      "dev": true,
      "dependencies": {
        "@types/json-schema": "^7.0.5",
        "ajv": "^6.12.4",
        "ajv-keywords": "^3.5.2"
      },
      "engines": {
        "node": ">= 8.9.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/webpack"
      }
    },
    "node_modules/schema-utils/node_modules/ajv": {
      "version": "6.12.6",
      "resolved": "https://registry.npmjs.org/ajv/-/ajv-6.12.6.tgz",
      "integrity": "sha512-j3fVLgvTo527anyYyJOGTYJbG+vnnQYvE0m5mmkc1TK+nxAppkCLMIL0aZ4dblVCNoGShhm+kzE4ZUykBoMg4g==",
      "dev": true,
      "dependencies": {
        "fast-deep-equal": "^3.1.1",
        "fast-json-stable-stringify": "^2.0.0",
        "json-schema-traverse": "^0.4.1",
        "uri-js": "^4.2.2"
      },
      "funding": {
        "type": "github",
        "url": "https://github.com/sponsors/epoberezkin"
      }
    },
    "node_modules/schema-utils/node_modules/ajv-keywords": {
      "version": "3.5.2",
      "resolved": "https://registry.npmjs.org/ajv-keywords/-/ajv-keywords-3.5.2.tgz",
      "integrity": "sha512-5p6WTN0DdTGVQk6VjcEju19IgaHudalcfabD7yhDGeA6bcQnmL+CpveLJq/3hvfwd1aof6L386Ougkx6RfyMIQ==",
      "dev": true,
      "peerDependencies": {
        "ajv": "^6.9.1"
      }
    },
    "node_modules/schema-utils/node_modules/json-schema-traverse": {
      "version": "0.4.1",
      "resolved": "https://registry.npmjs.org/json-schema-traverse/-/json-schema-traverse-0.4.1.tgz",
      "integrity": "sha512-xbbCH5dCYU5T8LcEhhuh7HJ88HXuW3qsI3Y0zOZFKfZEHcpWiHU/Jxzk629Brsab/mMiHQti9wMP+845RPe3Vg==",
      "dev": true
    },
    "node_modules/select-hose": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/select-hose/-/select-hose-2.0.0.tgz",
      "integrity": "sha1-Yl2GWPhlr0Psliv8N2o3NZpJlMo=",
      "dev": true
    },
    "node_modules/selfsigned": {
      "version": "1.10.14",
      "resolved": "https://registry.npmjs.org/selfsigned/-/selfsigned-1.10.14.tgz",
      "integrity": "sha512-lkjaiAye+wBZDCBsu5BGi0XiLRxeUlsGod5ZP924CRSEoGuZAw/f7y9RKu28rwTfiHVhdavhB0qH0INV6P1lEA==",
      "dev": true,
      "dependencies": {
        "node-forge": "^0.10.0"
      }
    },
    "node_modules/semver": {
      "version": "7.3.5",
      "resolved": "https://registry.npmjs.org/semver/-/semver-7.3.5.tgz",
      "integrity": "sha512-PoeGJYh8HK4BTO/a9Tf6ZG3veo/A7ZVsYrSA6J8ny9nb3B1VrpkuN+z9OE5wfE5p6H4LchYZsegiQgbJD94ZFQ==",
      "dependencies": {
        "lru-cache": "^6.0.0"
      },
      "bin": {
        "semver": "bin/semver.js"
      },
      "engines": {
        "node": ">=10"
      }
    },
    "node_modules/semver-compare": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/semver-compare/-/semver-compare-1.0.0.tgz",
      "integrity": "sha1-De4hahyUGrN+nvsXiPavxf9VN/w="
    },
    "node_modules/semver-diff": {
      "version": "3.1.1",
      "resolved": "https://registry.npmjs.org/semver-diff/-/semver-diff-3.1.1.tgz",
      "integrity": "sha512-GX0Ix/CJcHyB8c4ykpHGIAvLyOwOobtM/8d+TQkAd81/bEjgPHrfba41Vpesr7jX/t8Uh+R3EX9eAS5be+jQYg==",
      "dependencies": {
        "semver": "^6.3.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/semver-diff/node_modules/semver": {
      "version": "6.3.0",
      "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.0.tgz",
      "integrity": "sha512-b39TBaTSfV6yBrapU89p5fKekE2m/NwnDocOVruQFS1/veMgdzuPcnOM34M6CwxW8jH/lxEa5rBoDeUwu5HHTw==",
      "bin": {
        "semver": "bin/semver.js"
      }
    },
    "node_modules/send": {
      "version": "0.17.2",
      "resolved": "https://registry.npmjs.org/send/-/send-0.17.2.tgz",
      "integrity": "sha512-UJYB6wFSJE3G00nEivR5rgWp8c2xXvJ3OPWPhmuteU0IKj8nKbG3DrjiOmLwpnHGYWAVwA69zmTm++YG0Hmwww==",
      "dependencies": {
        "debug": "2.6.9",
        "depd": "~1.1.2",
        "destroy": "~1.0.4",
        "encodeurl": "~1.0.2",
        "escape-html": "~1.0.3",
        "etag": "~1.8.1",
        "fresh": "0.5.2",
        "http-errors": "1.8.1",
        "mime": "1.6.0",
        "ms": "2.1.3",
        "on-finished": "~2.3.0",
        "range-parser": "~1.2.1",
        "statuses": "~1.5.0"
      },
      "engines": {
        "node": ">= 0.8.0"
      }
    },
    "node_modules/send/node_modules/debug": {
      "version": "2.6.9",
      "resolved": "https://registry.npmjs.org/debug/-/debug-2.6.9.tgz",
      "integrity": "sha512-bC7ElrdJaJnPbAP+1EotYvqZsb3ecl5wi6Bfi6BJTUcNowp6cvspg0jXznRTKDjm/E7AdgFBVeAPVMNcKGsHMA==",
      "dependencies": {
        "ms": "2.0.0"
      }
    },
    "node_modules/send/node_modules/debug/node_modules/ms": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/ms/-/ms-2.0.0.tgz",
      "integrity": "sha1-VgiurfwAvmwpAd9fmGF4jeDVl8g="
    },
    "node_modules/send/node_modules/mime": {
      "version": "1.6.0",
      "resolved": "https://registry.npmjs.org/mime/-/mime-1.6.0.tgz",
      "integrity": "sha512-x0Vn8spI+wuJ1O6S7gnbaQg8Pxh4NNHb7KSINmEWKiPE4RKOplvijn+NkmYmmRgP68mc70j2EbeTFRsrswaQeg==",
      "bin": {
        "mime": "cli.js"
      },
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/send/node_modules/ms": {
      "version": "2.1.3",
      "resolved": "https://registry.npmjs.org/ms/-/ms-2.1.3.tgz",
      "integrity": "sha512-6FlzubTLZG3J2a/NVCAleEhjzq5oxgHyaCU9yYXvcLsvoVaHJq/s5xXI6/XXP6tz7R9xAOtHnSO/tXtF3WRTlA=="
    },
    "node_modules/serialize-javascript": {
      "version": "6.0.0",
      "resolved": "https://registry.npmjs.org/serialize-javascript/-/serialize-javascript-6.0.0.tgz",
      "integrity": "sha512-Qr3TosvguFt8ePWqsvRfrKyQXIiW+nGbYpy8XK24NQHE83caxWt+mIymTT19DGFbNWNLfEwsrkSmN64lVWB9ag==",
      "dev": true,
      "dependencies": {
        "randombytes": "^2.1.0"
      }
    },
    "node_modules/serve-index": {
      "version": "1.9.1",
      "resolved": "https://registry.npmjs.org/serve-index/-/serve-index-1.9.1.tgz",
      "integrity": "sha1-03aNabHn2C5c4FD/9bRTvqEqkjk=",
      "dev": true,
      "dependencies": {
        "accepts": "~1.3.4",
        "batch": "0.6.1",
        "debug": "2.6.9",
        "escape-html": "~1.0.3",
        "http-errors": "~1.6.2",
        "mime-types": "~2.1.17",
        "parseurl": "~1.3.2"
      },
      "engines": {
        "node": ">= 0.8.0"
      }
    },
    "node_modules/serve-index/node_modules/debug": {
      "version": "2.6.9",
      "resolved": "https://registry.npmjs.org/debug/-/debug-2.6.9.tgz",
      "integrity": "sha512-bC7ElrdJaJnPbAP+1EotYvqZsb3ecl5wi6Bfi6BJTUcNowp6cvspg0jXznRTKDjm/E7AdgFBVeAPVMNcKGsHMA==",
      "dev": true,
      "dependencies": {
        "ms": "2.0.0"
      }
    },
    "node_modules/serve-index/node_modules/http-errors": {
      "version": "1.6.3",
      "resolved": "https://registry.npmjs.org/http-errors/-/http-errors-1.6.3.tgz",
      "integrity": "sha1-i1VoC7S+KDoLW/TqLjhYC+HZMg0=",
      "dev": true,
      "dependencies": {
        "depd": "~1.1.2",
        "inherits": "2.0.3",
        "setprototypeof": "1.1.0",
        "statuses": ">= 1.4.0 < 2"
      },
      "engines": {
        "node": ">= 0.6"
      }
    },
    "node_modules/serve-index/node_modules/inherits": {
      "version": "2.0.3",
      "resolved": "https://registry.npmjs.org/inherits/-/inherits-2.0.3.tgz",
      "integrity": "sha1-Yzwsg+PaQqUC9SRmAiSA9CCCYd4=",
      "dev": true
    },
    "node_modules/serve-index/node_modules/ms": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/ms/-/ms-2.0.0.tgz",
      "integrity": "sha1-VgiurfwAvmwpAd9fmGF4jeDVl8g=",
      "dev": true
    },
    "node_modules/serve-index/node_modules/setprototypeof": {
      "version": "1.1.0",
      "resolved": "https://registry.npmjs.org/setprototypeof/-/setprototypeof-1.1.0.tgz",
      "integrity": "sha512-BvE/TwpZX4FXExxOxZyRGQQv651MSwmWKZGqvmPcRIjDqWub67kTKuIMx43cZZrS/cBBzwBcNDWoFxt2XEFIpQ==",
      "dev": true
    },
    "node_modules/serve-static": {
      "version": "1.14.2",
      "resolved": "https://registry.npmjs.org/serve-static/-/serve-static-1.14.2.tgz",
      "integrity": "sha512-+TMNA9AFxUEGuC0z2mevogSnn9MXKb4fa7ngeRMJaaGv8vTwnIEkKi+QGvPt33HSnf8pRS+WGM0EbMtCJLKMBQ==",
      "dependencies": {
        "encodeurl": "~1.0.2",
        "escape-html": "~1.0.3",
        "parseurl": "~1.3.3",
        "send": "0.17.2"
      },
      "engines": {
        "node": ">= 0.8.0"
      }
    },
    "node_modules/server-destroy": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/server-destroy/-/server-destroy-1.0.1.tgz",
      "integrity": "sha1-8Tv5KOQrnD55OD5hzDmYtdFObN0="
    },
    "node_modules/set-blocking": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/set-blocking/-/set-blocking-2.0.0.tgz",
      "integrity": "sha1-BF+XgtARrppoA93TgrJDkrPYkPc=",
      "dev": true
    },
    "node_modules/setprototypeof": {
      "version": "1.2.0",
      "resolved": "https://registry.npmjs.org/setprototypeof/-/setprototypeof-1.2.0.tgz",
      "integrity": "sha512-E5LDX7Wrp85Kil5bhZv46j8jOeboKq5JMmYM3gVGdGH8xFpPWXUMsNrlODCrkoxMEeNi/XZIwuRvY4XNwYMJpw=="
    },
    "node_modules/shallow-clone": {
      "version": "3.0.1",
      "resolved": "https://registry.npmjs.org/shallow-clone/-/shallow-clone-3.0.1.tgz",
      "integrity": "sha512-/6KqX+GVUdqPuPPd2LxDDxzX6CAbjJehAAOKlNpqqUpAqPM6HeL8f+o3a+JsyGjn2lv0WY8UsTgUJjU9Ok55NA==",
      "dev": true,
      "dependencies": {
        "kind-of": "^6.0.2"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/shebang-command": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/shebang-command/-/shebang-command-2.0.0.tgz",
      "integrity": "sha512-kHxr2zZpYtdmrN1qDjrrX/Z1rR1kG8Dx+gkpK1G4eXmvXswmcE1hTWBWYUzlraYw1/yZp6YuDY77YtvbN0dmDA==",
      "dev": true,
      "dependencies": {
        "shebang-regex": "^3.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/shebang-regex": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/shebang-regex/-/shebang-regex-3.0.0.tgz",
      "integrity": "sha512-7++dFhtcx3353uBaq8DDR4NuxBetBzC7ZQOhmTQInHEd6bSrXdiEyzCvG07Z44UYdLShWUyXt5M/yhz8ekcb1A==",
      "dev": true,
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/signal-exit": {
      "version": "3.0.6",
      "resolved": "https://registry.npmjs.org/signal-exit/-/signal-exit-3.0.6.tgz",
      "integrity": "sha512-sDl4qMFpijcGw22U5w63KmD3cZJfBuFlVNbVMKje2keoKML7X2UzWbc4XrmEbDwg0NXJc3yv4/ox7b+JWb57kQ=="
    },
    "node_modules/slash": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/slash/-/slash-4.0.0.tgz",
      "integrity": "sha512-3dOsAHXXUkQTpOYcoAxLIorMTp4gIQr5IW3iVb7A7lFIp0VHhnynm9izx6TssdrIcVIESAlVjtnO2K8bg+Coew==",
      "dev": true,
      "engines": {
        "node": ">=12"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/smart-buffer": {
      "version": "4.2.0",
      "resolved": "https://registry.npmjs.org/smart-buffer/-/smart-buffer-4.2.0.tgz",
      "integrity": "sha512-94hK0Hh8rPqQl2xXc3HsaBoOXKV20MToPkcXvwbISWLEs+64sBq5kFgn2kJDHb1Pry9yrP0dxrCI9RRci7RXKg==",
      "dev": true,
      "engines": {
        "node": ">= 6.0.0",
        "npm": ">= 3.0.0"
      }
    },
    "node_modules/socket.io": {
      "version": "4.4.1",
      "resolved": "https://registry.npmjs.org/socket.io/-/socket.io-4.4.1.tgz",
      "integrity": "sha512-s04vrBswdQBUmuWJuuNTmXUVJhP0cVky8bBDhdkf8y0Ptsu7fKU2LuLbts9g+pdmAdyMMn8F/9Mf1/wbtUN0fg==",
      "dev": true,
      "dependencies": {
        "accepts": "~1.3.4",
        "base64id": "~2.0.0",
        "debug": "~4.3.2",
        "engine.io": "~6.1.0",
        "socket.io-adapter": "~2.3.3",
        "socket.io-parser": "~4.0.4"
      },
      "engines": {
        "node": ">=10.0.0"
      }
    },
    "node_modules/socket.io-adapter": {
      "version": "2.3.3",
      "resolved": "https://registry.npmjs.org/socket.io-adapter/-/socket.io-adapter-2.3.3.tgz",
      "integrity": "sha512-Qd/iwn3VskrpNO60BeRyCyr8ZWw9CPZyitW4AQwmRZ8zCiyDiL+znRnWX6tDHXnWn1sJrM1+b6Mn6wEDJJ4aYQ==",
      "dev": true
    },
    "node_modules/socket.io-parser": {
      "version": "4.0.4",
      "resolved": "https://registry.npmjs.org/socket.io-parser/-/socket.io-parser-4.0.4.tgz",
      "integrity": "sha512-t+b0SS+IxG7Rxzda2EVvyBZbvFPBCjJoyHuE0P//7OAsN23GItzDRdWa6ALxZI/8R5ygK7jAR6t028/z+7295g==",
      "dev": true,
      "dependencies": {
        "@types/component-emitter": "^1.2.10",
        "component-emitter": "~1.3.0",
        "debug": "~4.3.1"
      },
      "engines": {
        "node": ">=10.0.0"
      }
    },
    "node_modules/sockjs": {
      "version": "0.3.24",
      "resolved": "https://registry.npmjs.org/sockjs/-/sockjs-0.3.24.tgz",
      "integrity": "sha512-GJgLTZ7vYb/JtPSSZ10hsOYIvEYsjbNU+zPdIHcUaWVNUEPivzxku31865sSSud0Da0W4lEeOPlmw93zLQchuQ==",
      "dev": true,
      "dependencies": {
        "faye-websocket": "^0.11.3",
        "uuid": "^8.3.2",
        "websocket-driver": "^0.7.4"
      }
    },
    "node_modules/socks": {
      "version": "2.6.1",
      "resolved": "https://registry.npmjs.org/socks/-/socks-2.6.1.tgz",
      "integrity": "sha512-kLQ9N5ucj8uIcxrDwjm0Jsqk06xdpBjGNQtpXy4Q8/QY2k+fY7nZH8CARy+hkbG+SGAovmzzuauCpBlb8FrnBA==",
      "dev": true,
      "dependencies": {
        "ip": "^1.1.5",
        "smart-buffer": "^4.1.0"
      },
      "engines": {
        "node": ">= 10.13.0",
        "npm": ">= 3.0.0"
      }
    },
    "node_modules/socks-proxy-agent": {
      "version": "6.1.1",
      "resolved": "https://registry.npmjs.org/socks-proxy-agent/-/socks-proxy-agent-6.1.1.tgz",
      "integrity": "sha512-t8J0kG3csjA4g6FTbsMOWws+7R7vuRC8aQ/wy3/1OWmsgwA68zs/+cExQ0koSitUDXqhufF/YJr9wtNMZHw5Ew==",
      "dev": true,
      "dependencies": {
        "agent-base": "^6.0.2",
        "debug": "^4.3.1",
        "socks": "^2.6.1"
      },
      "engines": {
        "node": ">= 10"
      }
    },
    "node_modules/source-map": {
      "version": "0.7.3",
      "resolved": "https://registry.npmjs.org/source-map/-/source-map-0.7.3.tgz",
      "integrity": "sha512-CkCj6giN3S+n9qrYiBTX5gystlENnRW5jZeNLHpe6aue+SrHcG5VYwujhW9s4dY31mEGsxBDrHR6oI69fTXsaQ==",
      "dev": true,
      "engines": {
        "node": ">= 8"
      }
    },
    "node_modules/source-map-js": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/source-map-js/-/source-map-js-1.0.2.tgz",
      "integrity": "sha512-R0XvVJ9WusLiqTCEiGCmICCMplcCkIwwR11mOSD9CR5u+IXYdiseeEuXCVAjS54zqwkLcPNnmU4OeJ6tUrWhDw==",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/source-map-loader": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/source-map-loader/-/source-map-loader-3.0.0.tgz",
      "integrity": "sha512-GKGWqWvYr04M7tn8dryIWvb0s8YM41z82iQv01yBtIylgxax0CwvSy6gc2Y02iuXwEfGWRlMicH0nvms9UZphw==",
      "dev": true,
      "dependencies": {
        "abab": "^2.0.5",
        "iconv-lite": "^0.6.2",
        "source-map-js": "^0.6.2"
      },
      "engines": {
        "node": ">= 12.13.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/webpack"
      },
      "peerDependencies": {
        "webpack": "^5.0.0"
      }
    },
    "node_modules/source-map-loader/node_modules/iconv-lite": {
      "version": "0.6.3",
      "resolved": "https://registry.npmjs.org/iconv-lite/-/iconv-lite-0.6.3.tgz",
      "integrity": "sha512-4fCk79wshMdzMp2rH06qWrJE4iolqLhCUH+OiuIgU++RB0+94NlDL81atO7GX55uUKueo0txHNtvEyI6D7WdMw==",
      "dev": true,
      "dependencies": {
        "safer-buffer": ">= 2.1.2 < 3.0.0"
      },
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/source-map-loader/node_modules/source-map-js": {
      "version": "0.6.2",
      "resolved": "https://registry.npmjs.org/source-map-js/-/source-map-js-0.6.2.tgz",
      "integrity": "sha512-/3GptzWzu0+0MBQFrDKzw/DvvMTUORvgY6k6jd/VS6iCR4RDTKWH6v6WPwQoUO8667uQEf9Oe38DxAYWY5F/Ug==",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/source-map-resolve": {
      "version": "0.6.0",
      "resolved": "https://registry.npmjs.org/source-map-resolve/-/source-map-resolve-0.6.0.tgz",
      "integrity": "sha512-KXBr9d/fO/bWo97NXsPIAW1bFSBOuCnjbNTBMO7N59hsv5i9yzRDfcYwwt0l04+VqnKC+EwzvJZIP/qkuMgR/w==",
      "deprecated": "See https://github.com/lydell/source-map-resolve#deprecated",
      "dev": true,
      "dependencies": {
        "atob": "^2.1.2",
        "decode-uri-component": "^0.2.0"
      }
    },
    "node_modules/source-map-support": {
      "version": "0.5.21",
      "resolved": "https://registry.npmjs.org/source-map-support/-/source-map-support-0.5.21.tgz",
      "integrity": "sha512-uBHU3L3czsIyYXKX88fdrGovxdSCoTGDRZ6SYXtSRxLZUzHg5P/66Ht6uoUlHu9EZod+inXhKo3qQgwXUT/y1w==",
      "dev": true,
      "dependencies": {
        "buffer-from": "^1.0.0",
        "source-map": "^0.6.0"
      }
    },
    "node_modules/source-map-support/node_modules/source-map": {
      "version": "0.6.1",
      "resolved": "https://registry.npmjs.org/source-map/-/source-map-0.6.1.tgz",
      "integrity": "sha512-UjgapumWlbMhkBgzT7Ykc5YXUT46F0iKu8SGXq0bcwP5dz/h0Plj6enJqjz1Zbq2l5WaqYnrVbwWOWMyF3F47g==",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/sourcemap-codec": {
      "version": "1.4.8",
      "resolved": "https://registry.npmjs.org/sourcemap-codec/-/sourcemap-codec-1.4.8.tgz",
      "integrity": "sha512-9NykojV5Uih4lgo5So5dtw+f0JgJX30KCNI8gwhz2J9A15wD0Ml6tjHKwf6fTSa6fAdVBdZeNOs9eJ71qCk8vA==",
      "dev": true
    },
    "node_modules/spdy": {
      "version": "4.0.2",
      "resolved": "https://registry.npmjs.org/spdy/-/spdy-4.0.2.tgz",
      "integrity": "sha512-r46gZQZQV+Kl9oItvl1JZZqJKGr+oEkB08A6BzkiR7593/7IbtuncXHd2YoYeTsG4157ZssMu9KYvUHLcjcDoA==",
      "dev": true,
      "dependencies": {
        "debug": "^4.1.0",
        "handle-thing": "^2.0.0",
        "http-deceiver": "^1.2.7",
        "select-hose": "^2.0.0",
        "spdy-transport": "^3.0.0"
      },
      "engines": {
        "node": ">=6.0.0"
      }
    },
    "node_modules/spdy-transport": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/spdy-transport/-/spdy-transport-3.0.0.tgz",
      "integrity": "sha512-hsLVFE5SjA6TCisWeJXFKniGGOpBgMLmerfO2aCyCU5s7nJ/rpAepqmFifv/GCbSbueEeAJJnmSQ2rKC/g8Fcw==",
      "dev": true,
      "dependencies": {
        "debug": "^4.1.0",
        "detect-node": "^2.0.4",
        "hpack.js": "^2.1.6",
        "obuf": "^1.1.2",
        "readable-stream": "^3.0.6",
        "wbuf": "^1.7.3"
      }
    },
    "node_modules/sprintf-js": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/sprintf-js/-/sprintf-js-1.0.3.tgz",
      "integrity": "sha1-BOaSb2YolTVPPdAVIDYzuFcpfiw=",
      "dev": true
    },
    "node_modules/ssri": {
      "version": "8.0.1",
      "resolved": "https://registry.npmjs.org/ssri/-/ssri-8.0.1.tgz",
      "integrity": "sha512-97qShzy1AiyxvPNIkLWoGua7xoQzzPjQ0HAH4B0rWKo7SZ6USuPcrUiAFrws0UH8RrbWmgq3LMTObhPIHbbBeQ==",
      "dev": true,
      "dependencies": {
        "minipass": "^3.1.1"
      },
      "engines": {
        "node": ">= 8"
      }
    },
    "node_modules/statuses": {
      "version": "1.5.0",
      "resolved": "https://registry.npmjs.org/statuses/-/statuses-1.5.0.tgz",
      "integrity": "sha1-Fhx9rBd2Wf2YEfQ3cfqZOBR4Yow=",
      "engines": {
        "node": ">= 0.6"
      }
    },
    "node_modules/steno": {
      "version": "0.4.4",
      "resolved": "https://registry.npmjs.org/steno/-/steno-0.4.4.tgz",
      "integrity": "sha1-BxEFvfwobmYVwEA8J+nXtdy4Vcs=",
      "dependencies": {
        "graceful-fs": "^4.1.3"
      }
    },
    "node_modules/streamroller": {
      "version": "3.0.2",
      "resolved": "https://registry.npmjs.org/streamroller/-/streamroller-3.0.2.tgz",
      "integrity": "sha512-ur6y5S5dopOaRXBuRIZ1u6GC5bcEXHRZKgfBjfCglMhmIf+roVCECjvkEYzNQOXIN2/JPnkMPW/8B3CZoKaEPA==",
      "dev": true,
      "dependencies": {
        "date-format": "^4.0.3",
        "debug": "^4.1.1",
        "fs-extra": "^10.0.0"
      },
      "engines": {
        "node": ">=8.0"
      }
    },
    "node_modules/string_decoder": {
      "version": "1.3.0",
      "resolved": "https://registry.npmjs.org/string_decoder/-/string_decoder-1.3.0.tgz",
      "integrity": "sha512-hkRX8U1WjJFd8LsDJ2yQ/wWWxaopEsABU1XfkM8A+j0+85JAGppt16cr1Whg6KIbb4okU6Mql6BOj+uup/wKeA==",
      "dev": true,
      "dependencies": {
        "safe-buffer": "~5.2.0"
      }
    },
    "node_modules/string_decoder/node_modules/safe-buffer": {
      "version": "5.2.1",
      "resolved": "https://registry.npmjs.org/safe-buffer/-/safe-buffer-5.2.1.tgz",
      "integrity": "sha512-rp3So07KcdmmKbGvgaNxQSJr7bGVSVk5S9Eq1F+ppbRo70+YeaDxkw5Dd8NPN+GD6bjnYm2VuPuCXmpuYvmCXQ==",
      "dev": true,
      "funding": [
        {
          "type": "github",
          "url": "https://github.com/sponsors/feross"
        },
        {
          "type": "patreon",
          "url": "https://www.patreon.com/feross"
        },
        {
          "type": "consulting",
          "url": "https://feross.org/support"
        }
      ]
    },
    "node_modules/string-width": {
      "version": "4.2.3",
      "resolved": "https://registry.npmjs.org/string-width/-/string-width-4.2.3.tgz",
      "integrity": "sha512-wKyQRQpjJ0sIp62ErSZdGsjMJWsap5oRNihHhu6G7JVO/9jIB6UyevL+tXuOqrng8j/cxKTWyWUwvSTriiZz/g==",
      "dependencies": {
        "emoji-regex": "^8.0.0",
        "is-fullwidth-code-point": "^3.0.0",
        "strip-ansi": "^6.0.1"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/strip-ansi": {
      "version": "6.0.1",
      "resolved": "https://registry.npmjs.org/strip-ansi/-/strip-ansi-6.0.1.tgz",
      "integrity": "sha512-Y38VPSHcqkFrCpFnQ9vuSXmquuv5oXOKpGeT6aGrr3o3Gc9AlVa6JBfUSOCnbxGGZF+/0ooI7KrPuUSztUdU5A==",
      "dependencies": {
        "ansi-regex": "^5.0.1"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/strip-final-newline": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/strip-final-newline/-/strip-final-newline-2.0.0.tgz",
      "integrity": "sha512-BrpvfNAE3dcvq7ll3xVumzjKjZQ5tI1sEUIKr3Uoks0XUl45St3FlatVqef9prk4jRDzhW6WZg+3bk93y6pLjA==",
      "dev": true,
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/strip-json-comments": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/strip-json-comments/-/strip-json-comments-2.0.1.tgz",
      "integrity": "sha1-PFMZQukIwml8DsNEhYwobHygpgo=",
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/stylus": {
      "version": "0.55.0",
      "resolved": "https://registry.npmjs.org/stylus/-/stylus-0.55.0.tgz",
      "integrity": "sha512-MuzIIVRSbc8XxHH7FjkvWqkIcr1BvoMZoR/oFuAJDlh7VSaNJzrB4uJ38GRQa+mWjLXODAMzeDe0xi9GYbGwnw==",
      "dev": true,
      "dependencies": {
        "css": "^3.0.0",
        "debug": "~3.1.0",
        "glob": "^7.1.6",
        "mkdirp": "~1.0.4",
        "safer-buffer": "^2.1.2",
        "sax": "~1.2.4",
        "semver": "^6.3.0",
        "source-map": "^0.7.3"
      },
      "bin": {
        "stylus": "bin/stylus"
      },
      "engines": {
        "node": "*"
      }
    },
    "node_modules/stylus-loader": {
      "version": "6.2.0",
      "resolved": "https://registry.npmjs.org/stylus-loader/-/stylus-loader-6.2.0.tgz",
      "integrity": "sha512-5dsDc7qVQGRoc6pvCL20eYgRUxepZ9FpeK28XhdXaIPP6kXr6nI1zAAKFQgP5OBkOfKaURp4WUpJzspg1f01Gg==",
      "dev": true,
      "dependencies": {
        "fast-glob": "^3.2.7",
        "klona": "^2.0.4",
        "normalize-path": "^3.0.0"
      },
      "engines": {
        "node": ">= 12.13.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/webpack"
      },
      "peerDependencies": {
        "stylus": ">=0.52.4",
        "webpack": "^5.0.0"
      }
    },
    "node_modules/stylus/node_modules/debug": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/debug/-/debug-3.1.0.tgz",
      "integrity": "sha512-OX8XqP7/1a9cqkxYw2yXss15f26NKWBpDXQd0/uK/KPqdQhxbPa994hnzjcE2VqQpDslf55723cKPUOGSmMY3g==",
      "dev": true,
      "dependencies": {
        "ms": "2.0.0"
      }
    },
    "node_modules/stylus/node_modules/ms": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/ms/-/ms-2.0.0.tgz",
      "integrity": "sha1-VgiurfwAvmwpAd9fmGF4jeDVl8g=",
      "dev": true
    },
    "node_modules/stylus/node_modules/semver": {
      "version": "6.3.0",
      "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.0.tgz",
      "integrity": "sha512-b39TBaTSfV6yBrapU89p5fKekE2m/NwnDocOVruQFS1/veMgdzuPcnOM34M6CwxW8jH/lxEa5rBoDeUwu5HHTw==",
      "dev": true,
      "bin": {
        "semver": "bin/semver.js"
      }
    },
    "node_modules/supports-color": {
      "version": "5.5.0",
      "resolved": "https://registry.npmjs.org/supports-color/-/supports-color-5.5.0.tgz",
      "integrity": "sha512-QjVjwdXIt408MIiAqCX4oUKsgU2EqAGzs2Ppkm4aQYbjm+ZEWEcW4SfFNTr4uMNZma0ey4f5lgLrkB0aX0QMow==",
      "dev": true,
      "dependencies": {
        "has-flag": "^3.0.0"
      },
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/symbol-observable": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/symbol-observable/-/symbol-observable-4.0.0.tgz",
      "integrity": "sha512-b19dMThMV4HVFynSAM1++gBHAbk2Tc/osgLIBZMKsyqh34jb2e8Os7T6ZW/Bt3pJFdBTd2JwAnAAEQV7rSNvcQ==",
      "dev": true,
      "engines": {
        "node": ">=0.10"
      }
    },
    "node_modules/tapable": {
      "version": "2.2.1",
      "resolved": "https://registry.npmjs.org/tapable/-/tapable-2.2.1.tgz",
      "integrity": "sha512-GNzQvQTOIP6RyTfE2Qxb8ZVlNmw0n88vp1szwWRimP02mnTsx3Wtn5qRdqY9w2XduFNUgvOwhNnQsjwCp+kqaQ==",
      "dev": true,
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/tar": {
      "version": "6.1.11",
      "resolved": "https://registry.npmjs.org/tar/-/tar-6.1.11.tgz",
      "integrity": "sha512-an/KZQzQUkZCkuoAA64hM92X0Urb6VpRhAFllDzz44U2mcD5scmT3zBc4VgVpkugF580+DQn8eAFSyoQt0tznA==",
      "dev": true,
      "dependencies": {
        "chownr": "^2.0.0",
        "fs-minipass": "^2.0.0",
        "minipass": "^3.0.0",
        "minizlib": "^2.1.1",
        "mkdirp": "^1.0.3",
        "yallist": "^4.0.0"
      },
      "engines": {
        "node": ">= 10"
      }
    },
    "node_modules/terser": {
      "version": "5.10.0",
      "resolved": "https://registry.npmjs.org/terser/-/terser-5.10.0.tgz",
      "integrity": "sha512-AMmF99DMfEDiRJfxfY5jj5wNH/bYO09cniSqhfoyxc8sFoYIgkJy86G04UoZU5VjlpnplVu0K6Tx6E9b5+DlHA==",
      "dev": true,
      "dependencies": {
        "commander": "^2.20.0",
        "source-map": "~0.7.2",
        "source-map-support": "~0.5.20"
      },
      "bin": {
        "terser": "bin/terser"
      },
      "engines": {
        "node": ">=10"
      },
      "peerDependencies": {
        "acorn": "^8.5.0"
      },
      "peerDependenciesMeta": {
        "acorn": {
          "optional": true
        }
      }
    },
    "node_modules/terser-webpack-plugin": {
      "version": "5.3.0",
      "resolved": "https://registry.npmjs.org/terser-webpack-plugin/-/terser-webpack-plugin-5.3.0.tgz",
      "integrity": "sha512-LPIisi3Ol4chwAaPP8toUJ3L4qCM1G0wao7L3qNv57Drezxj6+VEyySpPw4B1HSO2Eg/hDY/MNF5XihCAoqnsQ==",
      "dev": true,
      "dependencies": {
        "jest-worker": "^27.4.1",
        "schema-utils": "^3.1.1",
        "serialize-javascript": "^6.0.0",
        "source-map": "^0.6.1",
        "terser": "^5.7.2"
      },
      "engines": {
        "node": ">= 10.13.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/webpack"
      },
      "peerDependencies": {
        "webpack": "^5.1.0"
      },
      "peerDependenciesMeta": {
        "@swc/core": {
          "optional": true
        },
        "esbuild": {
          "optional": true
        },
        "uglify-js": {
          "optional": true
        }
      }
    },
    "node_modules/terser-webpack-plugin/node_modules/ajv": {
      "version": "6.12.6",
      "resolved": "https://registry.npmjs.org/ajv/-/ajv-6.12.6.tgz",
      "integrity": "sha512-j3fVLgvTo527anyYyJOGTYJbG+vnnQYvE0m5mmkc1TK+nxAppkCLMIL0aZ4dblVCNoGShhm+kzE4ZUykBoMg4g==",
      "dev": true,
      "dependencies": {
        "fast-deep-equal": "^3.1.1",
        "fast-json-stable-stringify": "^2.0.0",
        "json-schema-traverse": "^0.4.1",
        "uri-js": "^4.2.2"
      },
      "funding": {
        "type": "github",
        "url": "https://github.com/sponsors/epoberezkin"
      }
    },
    "node_modules/terser-webpack-plugin/node_modules/ajv-keywords": {
      "version": "3.5.2",
      "resolved": "https://registry.npmjs.org/ajv-keywords/-/ajv-keywords-3.5.2.tgz",
      "integrity": "sha512-5p6WTN0DdTGVQk6VjcEju19IgaHudalcfabD7yhDGeA6bcQnmL+CpveLJq/3hvfwd1aof6L386Ougkx6RfyMIQ==",
      "dev": true,
      "peerDependencies": {
        "ajv": "^6.9.1"
      }
    },
    "node_modules/terser-webpack-plugin/node_modules/json-schema-traverse": {
      "version": "0.4.1",
      "resolved": "https://registry.npmjs.org/json-schema-traverse/-/json-schema-traverse-0.4.1.tgz",
      "integrity": "sha512-xbbCH5dCYU5T8LcEhhuh7HJ88HXuW3qsI3Y0zOZFKfZEHcpWiHU/Jxzk629Brsab/mMiHQti9wMP+845RPe3Vg==",
      "dev": true
    },
    "node_modules/terser-webpack-plugin/node_modules/schema-utils": {
      "version": "3.1.1",
      "resolved": "https://registry.npmjs.org/schema-utils/-/schema-utils-3.1.1.tgz",
      "integrity": "sha512-Y5PQxS4ITlC+EahLuXaY86TXfR7Dc5lw294alXOq86JAHCihAIZfqv8nNCWvaEJvaC51uN9hbLGeV0cFBdH+Fw==",
      "dev": true,
      "dependencies": {
        "@types/json-schema": "^7.0.8",
        "ajv": "^6.12.5",
        "ajv-keywords": "^3.5.2"
      },
      "engines": {
        "node": ">= 10.13.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/webpack"
      }
    },
    "node_modules/terser-webpack-plugin/node_modules/source-map": {
      "version": "0.6.1",
      "resolved": "https://registry.npmjs.org/source-map/-/source-map-0.6.1.tgz",
      "integrity": "sha512-UjgapumWlbMhkBgzT7Ykc5YXUT46F0iKu8SGXq0bcwP5dz/h0Plj6enJqjz1Zbq2l5WaqYnrVbwWOWMyF3F47g==",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/test-exclude": {
      "version": "6.0.0",
      "resolved": "https://registry.npmjs.org/test-exclude/-/test-exclude-6.0.0.tgz",
      "integrity": "sha512-cAGWPIyOHU6zlmg88jwm7VRyXnMN7iV68OGAbYDk/Mh/xC/pzVPlQtY6ngoIH/5/tciuhGfvESU8GrHrcxD56w==",
      "dev": true,
      "dependencies": {
        "@istanbuljs/schema": "^0.1.2",
        "glob": "^7.1.4",
        "minimatch": "^3.0.4"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/text-table": {
      "version": "0.2.0",
      "resolved": "https://registry.npmjs.org/text-table/-/text-table-0.2.0.tgz",
      "integrity": "sha1-f17oI66AUgfACvLfSoTsP8+lcLQ=",
      "dev": true
    },
    "node_modules/through": {
      "version": "2.3.8",
      "resolved": "https://registry.npmjs.org/through/-/through-2.3.8.tgz",
      "integrity": "sha1-DdTJ/6q8NXlgsbckEV1+Doai4fU=",
      "dev": true
    },
    "node_modules/thunky": {
      "version": "1.1.0",
      "resolved": "https://registry.npmjs.org/thunky/-/thunky-1.1.0.tgz",
      "integrity": "sha512-eHY7nBftgThBqOyHGVN+l8gF0BucP09fMo0oO/Lb0w1OF80dJv+lDVpXG60WMQvkcxAkNybKsrEIE3ZtKGmPrA==",
      "dev": true
    },
    "node_modules/tmp": {
      "version": "0.0.33",
      "resolved": "https://registry.npmjs.org/tmp/-/tmp-0.0.33.tgz",
      "integrity": "sha512-jRCJlojKnZ3addtTOjdIqoRuPEKBvNXcGYqzO6zWZX8KfKEpnGY5jfggJQ3EjKuu8D4bJRr0y+cYJFmYbImXGw==",
      "dev": true,
      "dependencies": {
        "os-tmpdir": "~1.0.2"
      },
      "engines": {
        "node": ">=0.6.0"
      }
    },
    "node_modules/to-fast-properties": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/to-fast-properties/-/to-fast-properties-2.0.0.tgz",
      "integrity": "sha1-3F5pjL0HkmW8c+A3doGk5Og/YW4=",
      "dev": true,
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/to-readable-stream": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/to-readable-stream/-/to-readable-stream-1.0.0.tgz",
      "integrity": "sha512-Iq25XBt6zD5npPhlLVXGFN3/gyR2/qODcKNNyTMd4vbm39HUaOiAM4PMq0eMVC/Tkxz+Zjdsc55g9yyz+Yq00Q==",
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/to-regex-range": {
      "version": "5.0.1",
      "resolved": "https://registry.npmjs.org/to-regex-range/-/to-regex-range-5.0.1.tgz",
      "integrity": "sha512-65P7iz6X5yEr1cwcgvQxbbIw7Uk3gOy5dIdtZ4rDveLqhrdJP+Li/Hx6tyK0NEb+2GCyneCMJiGqrADCSNk8sQ==",
      "dev": true,
      "dependencies": {
        "is-number": "^7.0.0"
      },
      "engines": {
        "node": ">=8.0"
      }
    },
    "node_modules/toidentifier": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/toidentifier/-/toidentifier-1.0.1.tgz",
      "integrity": "sha512-o5sSPKEkg/DIQNmH43V0/uerLrpzVedkUh8tGNvaeXpfpuwjKenlSox/2O/BTlZUtEe+JG7s5YhEz608PlAHRA==",
      "engines": {
        "node": ">=0.6"
      }
    },
    "node_modules/tree-kill": {
      "version": "1.2.2",
      "resolved": "https://registry.npmjs.org/tree-kill/-/tree-kill-1.2.2.tgz",
      "integrity": "sha512-L0Orpi8qGpRG//Nd+H90vFB+3iHnue1zSSGmNOOCh1GLJ7rUKVwV2HvijphGQS2UmhUZewS9VgvxYIdgr+fG1A==",
      "dev": true,
      "bin": {
        "tree-kill": "cli.js"
      }
    },
    "node_modules/tslib": {
      "version": "2.3.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.3.1.tgz",
      "integrity": "sha512-77EbyPPpMz+FRFRuAFlWMtmgUWGe9UOG2Z25NqCwiIjRhOf5iKGuzSe5P2w1laq+FkRy4p+PCuVkJSGkzTEKVw=="
    },
    "node_modules/type-fest": {
      "version": "0.21.3",
      "resolved": "https://registry.npmjs.org/type-fest/-/type-fest-0.21.3.tgz",
      "integrity": "sha512-t0rzBq87m3fVcduHDUFhKmyyX+9eo6WQjZvf51Ea/M0Q7+T374Jp1aUiyUl0GKxp8M/OETVHSDvmkyPgvX+X2w==",
      "dev": true,
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/type-is": {
      "version": "1.6.18",
      "resolved": "https://registry.npmjs.org/type-is/-/type-is-1.6.18.tgz",
      "integrity": "sha512-TkRKr9sUTxEH8MdfuCSP7VizJyzRNMjj2J2do2Jr3Kym598JVdEksuzPQCnlFPW4ky9Q+iA+ma9BGm06XQBy8g==",
      "dependencies": {
        "media-typer": "0.3.0",
        "mime-types": "~2.1.24"
      },
      "engines": {
        "node": ">= 0.6"
      }
    },
    "node_modules/typed-assert": {
      "version": "1.0.8",
      "resolved": "https://registry.npmjs.org/typed-assert/-/typed-assert-1.0.8.tgz",
      "integrity": "sha512-5NkbXZUlmCE73Fs7gvkp1XXJWHYetPkg60QnQ2NXQmBYNFxbBr2zA8GCtaH4K2s2WhOmSlgiSTmrjrcm5tnM5g==",
      "dev": true
    },
    "node_modules/typedarray-to-buffer": {
      "version": "3.1.5",
      "resolved": "https://registry.npmjs.org/typedarray-to-buffer/-/typedarray-to-buffer-3.1.5.tgz",
      "integrity": "sha512-zdu8XMNEDepKKR+XYOXAVPtWui0ly0NtohUscw+UmaHiAWT8hrV1rr//H6V+0DvJ3OQ19S979M0laLfX8rm82Q==",
      "dependencies": {
        "is-typedarray": "^1.0.0"
      }
    },
    "node_modules/typescript": {
      "version": "4.5.5",
      "resolved": "https://registry.npmjs.org/typescript/-/typescript-4.5.5.tgz",
      "integrity": "sha512-TCTIul70LyWe6IJWT8QSYeA54WQe8EjQFU4wY52Fasj5UKx88LNYKCgBEHcOMOrFF1rKGbD8v/xcNWVUq9SymA==",
      "dev": true,
      "bin": {
        "tsc": "bin/tsc",
        "tsserver": "bin/tsserver"
      },
      "engines": {
        "node": ">=4.2.0"
      }
    },
    "node_modules/ua-parser-js": {
      "version": "0.7.31",
      "resolved": "https://registry.npmjs.org/ua-parser-js/-/ua-parser-js-0.7.31.tgz",
      "integrity": "sha512-qLK/Xe9E2uzmYI3qLeOmI0tEOt+TBBQyUIAh4aAgU05FVYzeZrKUdkAZfBNVGRaHVgV0TDkdEngJSw/SyQchkQ==",
      "dev": true,
      "funding": [
        {
          "type": "opencollective",
          "url": "https://opencollective.com/ua-parser-js"
        },
        {
          "type": "paypal",
          "url": "https://paypal.me/faisalman"
        }
      ],
      "engines": {
        "node": "*"
      }
    },
    "node_modules/unicode-canonical-property-names-ecmascript": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/unicode-canonical-property-names-ecmascript/-/unicode-canonical-property-names-ecmascript-2.0.0.tgz",
      "integrity": "sha512-yY5PpDlfVIU5+y/BSCxAJRBIS1Zc2dDG3Ujq+sR0U+JjUevW2JhocOF+soROYDSaAezOzOKuyyixhD6mBknSmQ==",
      "dev": true,
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/unicode-match-property-ecmascript": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/unicode-match-property-ecmascript/-/unicode-match-property-ecmascript-2.0.0.tgz",
      "integrity": "sha512-5kaZCrbp5mmbz5ulBkDkbY0SsPOjKqVS35VpL9ulMPfSl0J0Xsm+9Evphv9CoIZFwre7aJoa94AY6seMKGVN5Q==",
      "dev": true,
      "dependencies": {
        "unicode-canonical-property-names-ecmascript": "^2.0.0",
        "unicode-property-aliases-ecmascript": "^2.0.0"
      },
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/unicode-match-property-value-ecmascript": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/unicode-match-property-value-ecmascript/-/unicode-match-property-value-ecmascript-2.0.0.tgz",
      "integrity": "sha512-7Yhkc0Ye+t4PNYzOGKedDhXbYIBe1XEQYQxOPyhcXNMJ0WCABqqj6ckydd6pWRZTHV4GuCPKdBAUiMc60tsKVw==",
      "dev": true,
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/unicode-property-aliases-ecmascript": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/unicode-property-aliases-ecmascript/-/unicode-property-aliases-ecmascript-2.0.0.tgz",
      "integrity": "sha512-5Zfuy9q/DFr4tfO7ZPeVXb1aPoeQSdeFMLpYuFebehDAhbuevLs5yxSZmIFN1tP5F9Wl4IpJrYojg85/zgyZHQ==",
      "dev": true,
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/unique-filename": {
      "version": "1.1.1",
      "resolved": "https://registry.npmjs.org/unique-filename/-/unique-filename-1.1.1.tgz",
      "integrity": "sha512-Vmp0jIp2ln35UTXuryvjzkjGdRyf9b2lTXuSYUiPmzRcl3FDtYqAwOnTJkAngD9SWhnoJzDbTKwaOrZ+STtxNQ==",
      "dev": true,
      "dependencies": {
        "unique-slug": "^2.0.0"
      }
    },
    "node_modules/unique-slug": {
      "version": "2.0.2",
      "resolved": "https://registry.npmjs.org/unique-slug/-/unique-slug-2.0.2.tgz",
      "integrity": "sha512-zoWr9ObaxALD3DOPfjPSqxt4fnZiWblxHIgeWqW8x7UqDzEtHEQLzji2cuJYQFCU6KmoJikOYAZlrTHHebjx2w==",
      "dev": true,
      "dependencies": {
        "imurmurhash": "^0.1.4"
      }
    },
    "node_modules/unique-string": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/unique-string/-/unique-string-2.0.0.tgz",
      "integrity": "sha512-uNaeirEPvpZWSgzwsPGtU2zVSTrn/8L5q/IexZmH0eH6SA73CmAA5U4GwORTxQAZs95TAXLNqeLoPPNO5gZfWg==",
      "dependencies": {
        "crypto-random-string": "^2.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/universalify": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/universalify/-/universalify-2.0.0.tgz",
      "integrity": "sha512-hAZsKq7Yy11Zu1DE0OzWjw7nnLZmJZYTDZZyEFHZdUhV8FkH5MCfoU1XMaxXovpyW5nq5scPqq0ZDP9Zyl04oQ==",
      "dev": true,
      "engines": {
        "node": ">= 10.0.0"
      }
    },
    "node_modules/unpipe": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/unpipe/-/unpipe-1.0.0.tgz",
      "integrity": "sha1-sr9O6FFKrmFltIF4KdIbLvSZBOw=",
      "engines": {
        "node": ">= 0.8"
      }
    },
    "node_modules/update-notifier": {
      "version": "5.1.0",
      "resolved": "https://registry.npmjs.org/update-notifier/-/update-notifier-5.1.0.tgz",
      "integrity": "sha512-ItnICHbeMh9GqUy31hFPrD1kcuZ3rpxDZbf4KUDavXwS0bW5m7SLbDQpGX3UYr072cbrF5hFUs3r5tUsPwjfHw==",
      "dependencies": {
        "boxen": "^5.0.0",
        "chalk": "^4.1.0",
        "configstore": "^5.0.1",
        "has-yarn": "^2.1.0",
        "import-lazy": "^2.1.0",
        "is-ci": "^2.0.0",
        "is-installed-globally": "^0.4.0",
        "is-npm": "^5.0.0",
        "is-yarn-global": "^0.3.0",
        "latest-version": "^5.1.0",
        "pupa": "^2.1.1",
        "semver": "^7.3.4",
        "semver-diff": "^3.1.1",
        "xdg-basedir": "^4.0.0"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/yeoman/update-notifier?sponsor=1"
      }
    },
    "node_modules/update-notifier/node_modules/ansi-styles": {
      "version": "4.3.0",
      "resolved": "https://registry.npmjs.org/ansi-styles/-/ansi-styles-4.3.0.tgz",
      "integrity": "sha512-zbB9rCJAT1rbjiVDb2hqKFHNYLxgtk8NURxZ3IZwD3F6NtxbXZQCnnSi1Lkx+IDohdPlFp222wVALIheZJQSEg==",
      "dependencies": {
        "color-convert": "^2.0.1"
      },
      "engines": {
        "node": ">=8"
      },
      "funding": {
        "url": "https://github.com/chalk/ansi-styles?sponsor=1"
      }
    },
    "node_modules/update-notifier/node_modules/chalk": {
      "version": "4.1.2",
      "resolved": "https://registry.npmjs.org/chalk/-/chalk-4.1.2.tgz",
      "integrity": "sha512-oKnbhFyRIXpUuez8iBMmyEa4nbj4IOQyuhc/wy9kY7/WVPcwIO9VA668Pu8RkO7+0G76SLROeyw9CpQ061i4mA==",
      "dependencies": {
        "ansi-styles": "^4.1.0",
        "supports-color": "^7.1.0"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/chalk/chalk?sponsor=1"
      }
    },
    "node_modules/update-notifier/node_modules/color-convert": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/color-convert/-/color-convert-2.0.1.tgz",
      "integrity": "sha512-RRECPsj7iu/xb5oKYcsFHSppFNnsj/52OVTRKb4zP5onXwVF3zVmmToNcOfGC+CRDpfK/U584fMg38ZHCaElKQ==",
      "dependencies": {
        "color-name": "~1.1.4"
      },
      "engines": {
        "node": ">=7.0.0"
      }
    },
    "node_modules/update-notifier/node_modules/color-name": {
      "version": "1.1.4",
      "resolved": "https://registry.npmjs.org/color-name/-/color-name-1.1.4.tgz",
      "integrity": "sha512-dOy+3AuW3a2wNbZHIuMZpTcgjGuLU/uBL/ubcZF9OXbDo8ff4O8yVp5Bf0efS8uEoYo5q4Fx7dY9OgQGXgAsQA=="
    },
    "node_modules/update-notifier/node_modules/has-flag": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/has-flag/-/has-flag-4.0.0.tgz",
      "integrity": "sha512-EykJT/Q1KjTWctppgIAgfSO0tKVuZUjhgMr17kqTumMl6Afv3EISleU7qZUzoXDFTAHTDC4NOoG/ZxU3EvlMPQ==",
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/update-notifier/node_modules/supports-color": {
      "version": "7.2.0",
      "resolved": "https://registry.npmjs.org/supports-color/-/supports-color-7.2.0.tgz",
      "integrity": "sha512-qpCAvRl9stuOHveKsn7HncJRvv501qIacKzQlO/+Lwxc9+0q2wLyv4Dfvt80/DPn2pqOBsJdDiogXGR9+OvwRw==",
      "dependencies": {
        "has-flag": "^4.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/uri-js": {
      "version": "4.4.1",
      "resolved": "https://registry.npmjs.org/uri-js/-/uri-js-4.4.1.tgz",
      "integrity": "sha512-7rKUyy33Q1yc98pQ1DAmLtwX109F7TIfWlW1Ydo8Wl1ii1SeHieeh0HHfPeL2fMXK6z0s8ecKs9frCuLJvndBg==",
      "dev": true,
      "dependencies": {
        "punycode": "^2.1.0"
      }
    },
    "node_modules/url": {
      "version": "0.11.0",
      "resolved": "https://registry.npmjs.org/url/-/url-0.11.0.tgz",
      "integrity": "sha1-ODjpfPxgUh63PFJajlW/3Z4uKPE=",
      "dev": true,
      "dependencies": {
        "punycode": "1.3.2",
        "querystring": "0.2.0"
      }
    },
    "node_modules/url-parse-lax": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/url-parse-lax/-/url-parse-lax-3.0.0.tgz",
      "integrity": "sha1-FrXK/Afb42dsGxmZF3gj1lA6yww=",
      "dependencies": {
        "prepend-http": "^2.0.0"
      },
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/url/node_modules/punycode": {
      "version": "1.3.2",
      "resolved": "https://registry.npmjs.org/punycode/-/punycode-1.3.2.tgz",
      "integrity": "sha1-llOgNvt8HuQjQvIyXM7v6jkmxI0=",
      "dev": true
    },
    "node_modules/util-deprecate": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/util-deprecate/-/util-deprecate-1.0.2.tgz",
      "integrity": "sha1-RQ1Nyfpw3nMnYvvS1KKJgUGaDM8=",
      "dev": true
    },
    "node_modules/utils-merge": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/utils-merge/-/utils-merge-1.0.1.tgz",
      "integrity": "sha1-n5VxD1CiZ5R7LMwSR0HBAoQn5xM=",
      "engines": {
        "node": ">= 0.4.0"
      }
    },
    "node_modules/uuid": {
      "version": "8.3.2",
      "resolved": "https://registry.npmjs.org/uuid/-/uuid-8.3.2.tgz",
      "integrity": "sha512-+NYs2QeMWy+GWFOEm9xnn6HCDp0l7QBD7ml8zLUmJ+93Q5NF0NocErnwkTkXVFNiX3/fpC6afS8Dhb/gz7R7eg==",
      "dev": true,
      "bin": {
        "uuid": "dist/bin/uuid"
      }
    },
    "node_modules/validate-npm-package-name": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/validate-npm-package-name/-/validate-npm-package-name-3.0.0.tgz",
      "integrity": "sha1-X6kS2B630MdK/BQN5zF/DKffQ34=",
      "dev": true,
      "dependencies": {
        "builtins": "^1.0.3"
      }
    },
    "node_modules/vary": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/vary/-/vary-1.1.2.tgz",
      "integrity": "sha1-IpnwLG3tMNSllhsLn3RSShj2NPw=",
      "engines": {
        "node": ">= 0.8"
      }
    },
    "node_modules/void-elements": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/void-elements/-/void-elements-2.0.1.tgz",
      "integrity": "sha1-wGavtYK7HLQSjWDqkjkulNXp2+w=",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/watchpack": {
      "version": "2.3.1",
      "resolved": "https://registry.npmjs.org/watchpack/-/watchpack-2.3.1.tgz",
      "integrity": "sha512-x0t0JuydIo8qCNctdDrn1OzH/qDzk2+rdCOC3YzumZ42fiMqmQ7T3xQurykYMhYfHaPHTp4ZxAx2NfUo1K6QaA==",
      "dev": true,
      "dependencies": {
        "glob-to-regexp": "^0.4.1",
        "graceful-fs": "^4.1.2"
      },
      "engines": {
        "node": ">=10.13.0"
      }
    },
    "node_modules/wbuf": {
      "version": "1.7.3",
      "resolved": "https://registry.npmjs.org/wbuf/-/wbuf-1.7.3.tgz",
      "integrity": "sha512-O84QOnr0icsbFGLS0O3bI5FswxzRr8/gHwWkDlQFskhSPryQXvrTMxjxGP4+iWYoauLoBvfDpkrOauZ+0iZpDA==",
      "dev": true,
      "dependencies": {
        "minimalistic-assert": "^1.0.0"
      }
    },
    "node_modules/wcwidth": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/wcwidth/-/wcwidth-1.0.1.tgz",
      "integrity": "sha1-8LDc+RW8X/FSivrbLA4XtTLaL+g=",
      "dev": true,
      "dependencies": {
        "defaults": "^1.0.3"
      }
    },
    "node_modules/webpack": {
      "version": "5.65.0",
      "resolved": "https://registry.npmjs.org/webpack/-/webpack-5.65.0.tgz",
      "integrity": "sha512-Q5or2o6EKs7+oKmJo7LaqZaMOlDWQse9Tm5l1WAfU/ujLGN5Pb0SqGeVkN/4bpPmEqEP5RnVhiqsOtWtUVwGRw==",
      "dev": true,
      "dependencies": {
        "@types/eslint-scope": "^3.7.0",
        "@types/estree": "^0.0.50",
        "@webassemblyjs/ast": "1.11.1",
        "@webassemblyjs/wasm-edit": "1.11.1",
        "@webassemblyjs/wasm-parser": "1.11.1",
        "acorn": "^8.4.1",
        "acorn-import-assertions": "^1.7.6",
        "browserslist": "^4.14.5",
        "chrome-trace-event": "^1.0.2",
        "enhanced-resolve": "^5.8.3",
        "es-module-lexer": "^0.9.0",
        "eslint-scope": "5.1.1",
        "events": "^3.2.0",
        "glob-to-regexp": "^0.4.1",
        "graceful-fs": "^4.2.4",
        "json-parse-better-errors": "^1.0.2",
        "loader-runner": "^4.2.0",
        "mime-types": "^2.1.27",
        "neo-async": "^2.6.2",
        "schema-utils": "^3.1.0",
        "tapable": "^2.1.1",
        "terser-webpack-plugin": "^5.1.3",
        "watchpack": "^2.3.1",
        "webpack-sources": "^3.2.2"
      },
      "bin": {
        "webpack": "bin/webpack.js"
      },
      "engines": {
        "node": ">=10.13.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/webpack"
      },
      "peerDependenciesMeta": {
        "webpack-cli": {
          "optional": true
        }
      }
    },
    "node_modules/webpack-dev-middleware": {
      "version": "5.2.2",
      "resolved": "https://registry.npmjs.org/webpack-dev-middleware/-/webpack-dev-middleware-5.2.2.tgz",
      "integrity": "sha512-DjZyYrsHhkikAFNvSNKrpnziXukU1EChFAh9j4LAm6ndPLPW8cN0KhM7T+RAiOqsQ6ABfQ8hoKIs9IWMTjov+w==",
      "dev": true,
      "dependencies": {
        "colorette": "^2.0.10",
        "memfs": "^3.2.2",
        "mime-types": "^2.1.31",
        "range-parser": "^1.2.1",
        "schema-utils": "^4.0.0"
      },
      "engines": {
        "node": ">= 12.13.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/webpack"
      },
      "peerDependencies": {
        "webpack": "^4.0.0 || ^5.0.0"
      }
    },
    "node_modules/webpack-dev-middleware/node_modules/schema-utils": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/schema-utils/-/schema-utils-4.0.0.tgz",
      "integrity": "sha512-1edyXKgh6XnJsJSQ8mKWXnN/BVaIbFMLpouRUrXgVq7WYne5kw3MW7UPhO44uRXQSIpTSXoJbmrR2X0w9kUTyg==",
      "dev": true,
      "dependencies": {
        "@types/json-schema": "^7.0.9",
        "ajv": "^8.8.0",
        "ajv-formats": "^2.1.1",
        "ajv-keywords": "^5.0.0"
      },
      "engines": {
        "node": ">= 12.13.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/webpack"
      }
    },
    "node_modules/webpack-dev-server": {
      "version": "4.6.0",
      "resolved": "https://registry.npmjs.org/webpack-dev-server/-/webpack-dev-server-4.6.0.tgz",
      "integrity": "sha512-oojcBIKvx3Ya7qs1/AVWHDgmP1Xml8rGsEBnSobxU/UJSX1xP1GPM3MwsAnDzvqcVmVki8tV7lbcsjEjk0PtYg==",
      "dev": true,
      "dependencies": {
        "ansi-html-community": "^0.0.8",
        "bonjour": "^3.5.0",
        "chokidar": "^3.5.2",
        "colorette": "^2.0.10",
        "compression": "^1.7.4",
        "connect-history-api-fallback": "^1.6.0",
        "default-gateway": "^6.0.3",
        "del": "^6.0.0",
        "express": "^4.17.1",
        "graceful-fs": "^4.2.6",
        "html-entities": "^2.3.2",
        "http-proxy-middleware": "^2.0.0",
        "ipaddr.js": "^2.0.1",
        "open": "^8.0.9",
        "p-retry": "^4.5.0",
        "portfinder": "^1.0.28",
        "schema-utils": "^4.0.0",
        "selfsigned": "^1.10.11",
        "serve-index": "^1.9.1",
        "sockjs": "^0.3.21",
        "spdy": "^4.0.2",
        "strip-ansi": "^7.0.0",
        "url": "^0.11.0",
        "webpack-dev-middleware": "^5.2.1",
        "ws": "^8.1.0"
      },
      "bin": {
        "webpack-dev-server": "bin/webpack-dev-server.js"
      },
      "engines": {
        "node": ">= 12.13.0"
      },
      "peerDependencies": {
        "webpack": "^4.37.0 || ^5.0.0"
      },
      "peerDependenciesMeta": {
        "webpack-cli": {
          "optional": true
        }
      }
    },
    "node_modules/webpack-dev-server/node_modules/ansi-regex": {
      "version": "6.0.1",
      "resolved": "https://registry.npmjs.org/ansi-regex/-/ansi-regex-6.0.1.tgz",
      "integrity": "sha512-n5M855fKb2SsfMIiFFoVrABHJC8QtHwVx+mHWP3QcEqBHYienj5dHSgjbxtC0WEZXYt4wcD6zrQElDPhFuZgfA==",
      "dev": true,
      "engines": {
        "node": ">=12"
      },
      "funding": {
        "url": "https://github.com/chalk/ansi-regex?sponsor=1"
      }
    },
    "node_modules/webpack-dev-server/node_modules/schema-utils": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/schema-utils/-/schema-utils-4.0.0.tgz",
      "integrity": "sha512-1edyXKgh6XnJsJSQ8mKWXnN/BVaIbFMLpouRUrXgVq7WYne5kw3MW7UPhO44uRXQSIpTSXoJbmrR2X0w9kUTyg==",
      "dev": true,
      "dependencies": {
        "@types/json-schema": "^7.0.9",
        "ajv": "^8.8.0",
        "ajv-formats": "^2.1.1",
        "ajv-keywords": "^5.0.0"
      },
      "engines": {
        "node": ">= 12.13.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/webpack"
      }
    },
    "node_modules/webpack-dev-server/node_modules/strip-ansi": {
      "version": "7.0.1",
      "resolved": "https://registry.npmjs.org/strip-ansi/-/strip-ansi-7.0.1.tgz",
      "integrity": "sha512-cXNxvT8dFNRVfhVME3JAe98mkXDYN2O1l7jmcwMnOslDeESg1rF/OZMtK0nRAhiari1unG5cD4jG3rapUAkLbw==",
      "dev": true,
      "dependencies": {
        "ansi-regex": "^6.0.1"
      },
      "engines": {
        "node": ">=12"
      },
      "funding": {
        "url": "https://github.com/chalk/strip-ansi?sponsor=1"
      }
    },
    "node_modules/webpack-merge": {
      "version": "5.8.0",
      "resolved": "https://registry.npmjs.org/webpack-merge/-/webpack-merge-5.8.0.tgz",
      "integrity": "sha512-/SaI7xY0831XwP6kzuwhKWVKDP9t1QY1h65lAFLbZqMPIuYcD9QAW4u9STIbU9kaJbPBB/geU/gLr1wDjOhQ+Q==",
      "dev": true,
      "dependencies": {
        "clone-deep": "^4.0.1",
        "wildcard": "^2.0.0"
      },
      "engines": {
        "node": ">=10.0.0"
      }
    },
    "node_modules/webpack-sources": {
      "version": "3.2.3",
      "resolved": "https://registry.npmjs.org/webpack-sources/-/webpack-sources-3.2.3.tgz",
      "integrity": "sha512-/DyMEOrDgLKKIG0fmvtz+4dUX/3Ghozwgm6iPp8KRhvn+eQf9+Q7GWxVNMk3+uCPWfdXYC4ExGBckIXdFEfH1w==",
      "dev": true,
      "engines": {
        "node": ">=10.13.0"
      }
    },
    "node_modules/webpack-subresource-integrity": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/webpack-subresource-integrity/-/webpack-subresource-integrity-5.0.0.tgz",
      "integrity": "sha512-x9514FpLRydO+UAQ8DY4aLtCjxmdLkuQVcDFN1kGzuusREYJ1B0rzk/iIlWiL6dnvrhEGFj2+UsdxDkP8Z4UKg==",
      "dev": true,
      "dependencies": {
        "typed-assert": "^1.0.8"
      },
      "engines": {
        "node": ">= 12"
      },
      "peerDependencies": {
        "html-webpack-plugin": ">= 5.0.0-beta.1 < 6",
        "webpack": "^5.12.0"
      },
      "peerDependenciesMeta": {
        "html-webpack-plugin": {
          "optional": true
        }
      }
    },
    "node_modules/webpack/node_modules/ajv": {
      "version": "6.12.6",
      "resolved": "https://registry.npmjs.org/ajv/-/ajv-6.12.6.tgz",
      "integrity": "sha512-j3fVLgvTo527anyYyJOGTYJbG+vnnQYvE0m5mmkc1TK+nxAppkCLMIL0aZ4dblVCNoGShhm+kzE4ZUykBoMg4g==",
      "dev": true,
      "dependencies": {
        "fast-deep-equal": "^3.1.1",
        "fast-json-stable-stringify": "^2.0.0",
        "json-schema-traverse": "^0.4.1",
        "uri-js": "^4.2.2"
      },
      "funding": {
        "type": "github",
        "url": "https://github.com/sponsors/epoberezkin"
      }
    },
    "node_modules/webpack/node_modules/ajv-keywords": {
      "version": "3.5.2",
      "resolved": "https://registry.npmjs.org/ajv-keywords/-/ajv-keywords-3.5.2.tgz",
      "integrity": "sha512-5p6WTN0DdTGVQk6VjcEju19IgaHudalcfabD7yhDGeA6bcQnmL+CpveLJq/3hvfwd1aof6L386Ougkx6RfyMIQ==",
      "dev": true,
      "peerDependencies": {
        "ajv": "^6.9.1"
      }
    },
    "node_modules/webpack/node_modules/json-schema-traverse": {
      "version": "0.4.1",
      "resolved": "https://registry.npmjs.org/json-schema-traverse/-/json-schema-traverse-0.4.1.tgz",
      "integrity": "sha512-xbbCH5dCYU5T8LcEhhuh7HJ88HXuW3qsI3Y0zOZFKfZEHcpWiHU/Jxzk629Brsab/mMiHQti9wMP+845RPe3Vg==",
      "dev": true
    },
    "node_modules/webpack/node_modules/schema-utils": {
      "version": "3.1.1",
      "resolved": "https://registry.npmjs.org/schema-utils/-/schema-utils-3.1.1.tgz",
      "integrity": "sha512-Y5PQxS4ITlC+EahLuXaY86TXfR7Dc5lw294alXOq86JAHCihAIZfqv8nNCWvaEJvaC51uN9hbLGeV0cFBdH+Fw==",
      "dev": true,
      "dependencies": {
        "@types/json-schema": "^7.0.8",
        "ajv": "^6.12.5",
        "ajv-keywords": "^3.5.2"
      },
      "engines": {
        "node": ">= 10.13.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/webpack"
      }
    },
    "node_modules/websocket-driver": {
      "version": "0.7.4",
      "resolved": "https://registry.npmjs.org/websocket-driver/-/websocket-driver-0.7.4.tgz",
      "integrity": "sha512-b17KeDIQVjvb0ssuSDF2cYXSg2iztliJ4B9WdsuB6J952qCPKmnVq4DyW5motImXHDC1cBT/1UezrJVsKw5zjg==",
      "dev": true,
      "dependencies": {
        "http-parser-js": ">=0.5.1",
        "safe-buffer": ">=5.1.0",
        "websocket-extensions": ">=0.1.1"
      },
      "engines": {
        "node": ">=0.8.0"
      }
    },
    "node_modules/websocket-extensions": {
      "version": "0.1.4",
      "resolved": "https://registry.npmjs.org/websocket-extensions/-/websocket-extensions-0.1.4.tgz",
      "integrity": "sha512-OqedPIGOfsDlo31UNwYbCFMSaO9m9G/0faIHj5/dZFDMFqPTcx6UwqyOy3COEaEOg/9VsGIpdqn62W5KhoKSpg==",
      "dev": true,
      "engines": {
        "node": ">=0.8.0"
      }
    },
    "node_modules/which": {
      "version": "1.3.1",
      "resolved": "https://registry.npmjs.org/which/-/which-1.3.1.tgz",
      "integrity": "sha512-HxJdYWq1MTIQbJ3nw0cqssHoTNU267KlrDuGZ1WYlxDStUtKUhOaJmh112/TZmHxxUfuJqPXSOm7tDyas0OSIQ==",
      "dev": true,
      "dependencies": {
        "isexe": "^2.0.0"
      },
      "bin": {
        "which": "bin/which"
      }
    },
    "node_modules/wide-align": {
      "version": "1.1.5",
      "resolved": "https://registry.npmjs.org/wide-align/-/wide-align-1.1.5.tgz",
      "integrity": "sha512-eDMORYaPNZ4sQIuuYPDHdQvf4gyCF9rEEV/yPxGfwPkRodwEgiMUUXTx/dex+Me0wxx53S+NgUHaP7y3MGlDmg==",
      "dev": true,
      "dependencies": {
        "string-width": "^1.0.2 || 2 || 3 || 4"
      }
    },
    "node_modules/widest-line": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/widest-line/-/widest-line-3.1.0.tgz",
      "integrity": "sha512-NsmoXalsWVDMGupxZ5R08ka9flZjjiLvHVAWYOKtiKM8ujtZWr9cRffak+uSE48+Ob8ObalXpwyeUiyDD6QFgg==",
      "dependencies": {
        "string-width": "^4.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/wildcard": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/wildcard/-/wildcard-2.0.0.tgz",
      "integrity": "sha512-JcKqAHLPxcdb9KM49dufGXn2x3ssnfjbcaQdLlfZsL9rH9wgDQjUtDxbo8NE0F6SFvydeu1VhZe7hZuHsB2/pw==",
      "dev": true
    },
    "node_modules/wrap-ansi": {
      "version": "7.0.0",
      "resolved": "https://registry.npmjs.org/wrap-ansi/-/wrap-ansi-7.0.0.tgz",
      "integrity": "sha512-YVGIj2kamLSTxw6NsZjoBxfSwsn0ycdesmc4p+Q21c5zPuZ1pl+NfxVdxPtdHvmNVOQ6XSYG4AUtyt/Fi7D16Q==",
      "dependencies": {
        "ansi-styles": "^4.0.0",
        "string-width": "^4.1.0",
        "strip-ansi": "^6.0.0"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/chalk/wrap-ansi?sponsor=1"
      }
    },
    "node_modules/wrap-ansi/node_modules/ansi-styles": {
      "version": "4.3.0",
      "resolved": "https://registry.npmjs.org/ansi-styles/-/ansi-styles-4.3.0.tgz",
      "integrity": "sha512-zbB9rCJAT1rbjiVDb2hqKFHNYLxgtk8NURxZ3IZwD3F6NtxbXZQCnnSi1Lkx+IDohdPlFp222wVALIheZJQSEg==",
      "dependencies": {
        "color-convert": "^2.0.1"
      },
      "engines": {
        "node": ">=8"
      },
      "funding": {
        "url": "https://github.com/chalk/ansi-styles?sponsor=1"
      }
    },
    "node_modules/wrap-ansi/node_modules/color-convert": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/color-convert/-/color-convert-2.0.1.tgz",
      "integrity": "sha512-RRECPsj7iu/xb5oKYcsFHSppFNnsj/52OVTRKb4zP5onXwVF3zVmmToNcOfGC+CRDpfK/U584fMg38ZHCaElKQ==",
      "dependencies": {
        "color-name": "~1.1.4"
      },
      "engines": {
        "node": ">=7.0.0"
      }
    },
    "node_modules/wrap-ansi/node_modules/color-name": {
      "version": "1.1.4",
      "resolved": "https://registry.npmjs.org/color-name/-/color-name-1.1.4.tgz",
      "integrity": "sha512-dOy+3AuW3a2wNbZHIuMZpTcgjGuLU/uBL/ubcZF9OXbDo8ff4O8yVp5Bf0efS8uEoYo5q4Fx7dY9OgQGXgAsQA=="
    },
    "node_modules/wrappy": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/wrappy/-/wrappy-1.0.2.tgz",
      "integrity": "sha1-tSQ9jz7BqjXxNkYFvA0QNuMKtp8="
    },
    "node_modules/write-file-atomic": {
      "version": "3.0.3",
      "resolved": "https://registry.npmjs.org/write-file-atomic/-/write-file-atomic-3.0.3.tgz",
      "integrity": "sha512-AvHcyZ5JnSfq3ioSyjrBkH9yW4m7Ayk8/9My/DD9onKeu/94fwrMocemO2QAJFAlnnDN+ZDS+ZjAR5ua1/PV/Q==",
      "dependencies": {
        "imurmurhash": "^0.1.4",
        "is-typedarray": "^1.0.0",
        "signal-exit": "^3.0.2",
        "typedarray-to-buffer": "^3.1.5"
      }
    },
    "node_modules/ws": {
      "version": "8.2.3",
      "resolved": "https://registry.npmjs.org/ws/-/ws-8.2.3.tgz",
      "integrity": "sha512-wBuoj1BDpC6ZQ1B7DWQBYVLphPWkm8i9Y0/3YdHjHKHiohOJ1ws+3OccDWtH+PoC9DZD5WOTrJvNbWvjS6JWaA==",
      "dev": true,
      "engines": {
        "node": ">=10.0.0"
      },
      "peerDependencies": {
        "bufferutil": "^4.0.1",
        "utf-8-validate": "^5.0.2"
      },
      "peerDependenciesMeta": {
        "bufferutil": {
          "optional": true
        },
        "utf-8-validate": {
          "optional": true
        }
      }
    },
    "node_modules/xdg-basedir": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/xdg-basedir/-/xdg-basedir-4.0.0.tgz",
      "integrity": "sha512-PSNhEJDejZYV7h50BohL09Er9VaIefr2LMAf3OEmpCkjOi34eYyQYAXUTjEQtZJTKcF0E2UKTh+osDLsgNim9Q==",
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/y18n": {
      "version": "5.0.8",
      "resolved": "https://registry.npmjs.org/y18n/-/y18n-5.0.8.tgz",
      "integrity": "sha512-0pfFzegeDWJHJIAmTLRP2DwHjdF5s7jo9tuztdQxAhINCdvS+3nGINqPd00AphqJR/0LhANUS6/+7SCb98YOfA==",
      "engines": {
        "node": ">=10"
      }
    },
    "node_modules/yallist": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/yallist/-/yallist-4.0.0.tgz",
      "integrity": "sha512-3wdGidZyq5PB084XLES5TpOSRA3wjXAlIWMhum2kRcv/41Sn2emQ0dycQW4uZXLejwKvg6EsvbdlVL+FYEct7A=="
    },
    "node_modules/yaml": {
      "version": "1.10.2",
      "resolved": "https://registry.npmjs.org/yaml/-/yaml-1.10.2.tgz",
      "integrity": "sha512-r3vXyErRCYJ7wg28yvBY5VSoAF8ZvlcW9/BwUzEtUsjvX/DKs24dIkuwjtuprwJJHsbyUbLApepYTR1BN4uHrg==",
      "dev": true,
      "engines": {
        "node": ">= 6"
      }
    },
    "node_modules/yargs": {
      "version": "17.3.1",
      "resolved": "https://registry.npmjs.org/yargs/-/yargs-17.3.1.tgz",
      "integrity": "sha512-WUANQeVgjLbNsEmGk20f+nlHgOqzRFpiGWVaBrYGYIGANIIu3lWjoyi0fNlFmJkvfhCZ6BXINe7/W2O2bV4iaA==",
      "dependencies": {
        "cliui": "^7.0.2",
        "escalade": "^3.1.1",
        "get-caller-file": "^2.0.5",
        "require-directory": "^2.1.1",
        "string-width": "^4.2.3",
        "y18n": "^5.0.5",
        "yargs-parser": "^21.0.0"
      },
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/yargs-parser": {
      "version": "21.0.0",
      "resolved": "https://registry.npmjs.org/yargs-parser/-/yargs-parser-21.0.0.tgz",
      "integrity": "sha512-z9kApYUOCwoeZ78rfRYYWdiU/iNL6mwwYlkkZfJoyMR1xps+NEBX5X7XmRpxkZHhXJ6+Ey00IwKxBBSW9FIjyA==",
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/zone.js": {
      "version": "0.11.4",
      "resolved": "https://registry.npmjs.org/zone.js/-/zone.js-0.11.4.tgz",
      "integrity": "sha512-DDh2Ab+A/B+9mJyajPjHFPWfYU1H+pdun4wnnk0OcQTNjem1XQSZ2CDW+rfZEUDjv5M19SBqAkjZi0x5wuB5Qw==",
      "dependencies": {
        "tslib": "^2.0.0"
      }
    }
  },
  "dependencies": {
    "@ampproject/remapping": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/@ampproject/remapping/-/remapping-1.0.2.tgz",
      "integrity": "sha512-SncaVxs+E3EdoA9xJgHfWPxZfowAgeIsd71VpqCKP6KNKm6s7zSqqvUc70UpKUFsrV3dAmy6qxHoIj5NG+3DiA==",
      "dev": true,
      "requires": {
        "@jridgewell/resolve-uri": "1.0.0",
        "sourcemap-codec": "1.4.8"
      }
    },
    "@angular-devkit/architect": {
      "version": "0.1301.4",
      "resolved": "https://registry.npmjs.org/@angular-devkit/architect/-/architect-0.1301.4.tgz",
      "integrity": "sha512-p6G8CEMnE+gYwxRyEttj3QGsuNJ3Kusi7iwBIzWyf2RpJSdGzXdwUEiRGg6iS0YHFr06/ZFfAWfnM2DQvNm4TA==",
      "dev": true,
      "requires": {
        "@angular-devkit/core": "13.1.4",
        "rxjs": "6.6.7"
      },
      "dependencies": {
        "rxjs": {
          "version": "6.6.7",
          "resolved": "https://registry.npmjs.org/rxjs/-/rxjs-6.6.7.tgz",
          "integrity": "sha512-hTdwr+7yYNIT5n4AMYp85KA6yw2Va0FLa3Rguvbpa4W3I5xynaBZo41cM3XM+4Q6fRMj3sBYIR1VAmZMXYJvRQ==",
          "dev": true,
          "requires": {
            "tslib": "^1.9.0"
          }
        },
        "tslib": {
          "version": "1.14.1",
          "resolved": "https://registry.npmjs.org/tslib/-/tslib-1.14.1.tgz",
          "integrity": "sha512-Xni35NKzjgMrwevysHTCArtLDpPvye8zV/0E4EyYn43P7/7qvQwPh9BGkHewbMulVntbigmcT7rdX3BNo9wRJg==",
          "dev": true
        }
      }
    },
    "@angular-devkit/build-angular": {
      "version": "13.1.4",
      "resolved": "https://registry.npmjs.org/@angular-devkit/build-angular/-/build-angular-13.1.4.tgz",
      "integrity": "sha512-MTvlUCb02J4ODXDsnit4N0PR9PkpKeSYpTPueaSBuWTBeP3dvMPZQabvb3C5QT/5yUzBiXQZq11QYx3Gui4StA==",
      "dev": true,
      "requires": {
        "@ampproject/remapping": "1.0.2",
        "@angular-devkit/architect": "0.1301.4",
        "@angular-devkit/build-webpack": "0.1301.4",
        "@angular-devkit/core": "13.1.4",
        "@babel/core": "7.16.0",
        "@babel/generator": "7.16.0",
        "@babel/helper-annotate-as-pure": "7.16.0",
        "@babel/plugin-proposal-async-generator-functions": "7.16.4",
        "@babel/plugin-transform-async-to-generator": "7.16.0",
        "@babel/plugin-transform-runtime": "7.16.4",
        "@babel/preset-env": "7.16.4",
        "@babel/runtime": "7.16.3",
        "@babel/template": "7.16.0",
        "@discoveryjs/json-ext": "0.5.6",
        "@ngtools/webpack": "13.1.4",
        "ansi-colors": "4.1.1",
        "babel-loader": "8.2.3",
        "babel-plugin-istanbul": "6.1.1",
        "browserslist": "^4.9.1",
        "cacache": "15.3.0",
        "circular-dependency-plugin": "5.2.2",
        "copy-webpack-plugin": "10.0.0",
        "core-js": "3.19.3",
        "critters": "0.0.16",
        "css-loader": "6.5.1",
        "esbuild": "0.14.11",
        "esbuild-wasm": "0.14.11",
        "glob": "7.2.0",
        "https-proxy-agent": "5.0.0",
        "inquirer": "8.2.0",
        "jsonc-parser": "3.0.0",
        "karma-source-map-support": "1.4.0",
        "less": "4.1.2",
        "less-loader": "10.2.0",
        "license-webpack-plugin": "4.0.0",
        "loader-utils": "3.2.0",
        "mini-css-extract-plugin": "2.4.5",
        "minimatch": "3.0.4",
        "open": "8.4.0",
        "ora": "5.4.1",
        "parse5-html-rewriting-stream": "6.0.1",
        "piscina": "3.1.0",
        "postcss": "8.4.4",
        "postcss-import": "14.0.2",
        "postcss-loader": "6.2.1",
        "postcss-preset-env": "7.2.3",
        "regenerator-runtime": "0.13.9",
        "resolve-url-loader": "4.0.0",
        "rxjs": "6.6.7",
        "sass": "1.44.0",
        "sass-loader": "12.4.0",
        "semver": "7.3.5",
        "source-map-loader": "3.0.0",
        "source-map-support": "0.5.21",
        "stylus": "0.55.0",
        "stylus-loader": "6.2.0",
        "terser": "5.10.0",
        "text-table": "0.2.0",
        "tree-kill": "1.2.2",
        "tslib": "2.3.1",
        "webpack": "5.65.0",
        "webpack-dev-middleware": "5.2.2",
        "webpack-dev-server": "4.6.0",
        "webpack-merge": "5.8.0",
        "webpack-subresource-integrity": "5.0.0"
      },
      "dependencies": {
        "rxjs": {
          "version": "6.6.7",
          "resolved": "https://registry.npmjs.org/rxjs/-/rxjs-6.6.7.tgz",
          "integrity": "sha512-hTdwr+7yYNIT5n4AMYp85KA6yw2Va0FLa3Rguvbpa4W3I5xynaBZo41cM3XM+4Q6fRMj3sBYIR1VAmZMXYJvRQ==",
          "dev": true,
          "requires": {
            "tslib": "^1.9.0"
          },
          "dependencies": {
            "tslib": {
              "version": "1.14.1",
              "resolved": "https://registry.npmjs.org/tslib/-/tslib-1.14.1.tgz",
              "integrity": "sha512-Xni35NKzjgMrwevysHTCArtLDpPvye8zV/0E4EyYn43P7/7qvQwPh9BGkHewbMulVntbigmcT7rdX3BNo9wRJg==",
              "dev": true
            }
          }
        }
      }
    },
    "@angular-devkit/build-webpack": {
      "version": "0.1301.4",
      "resolved": "https://registry.npmjs.org/@angular-devkit/build-webpack/-/build-webpack-0.1301.4.tgz",
      "integrity": "sha512-IcC3Y5WhreIV0uT90ITqJVgRqFjGwH72hftwLxkslaX+FJDcL36mhsNdyN66BJiuX7R85xUxHq3PEb9cZrllJA==",
      "dev": true,
      "requires": {
        "@angular-devkit/architect": "0.1301.4",
        "rxjs": "6.6.7"
      },
      "dependencies": {
        "rxjs": {
          "version": "6.6.7",
          "resolved": "https://registry.npmjs.org/rxjs/-/rxjs-6.6.7.tgz",
          "integrity": "sha512-hTdwr+7yYNIT5n4AMYp85KA6yw2Va0FLa3Rguvbpa4W3I5xynaBZo41cM3XM+4Q6fRMj3sBYIR1VAmZMXYJvRQ==",
          "dev": true,
          "requires": {
            "tslib": "^1.9.0"
          }
        },
        "tslib": {
          "version": "1.14.1",
          "resolved": "https://registry.npmjs.org/tslib/-/tslib-1.14.1.tgz",
          "integrity": "sha512-Xni35NKzjgMrwevysHTCArtLDpPvye8zV/0E4EyYn43P7/7qvQwPh9BGkHewbMulVntbigmcT7rdX3BNo9wRJg==",
          "dev": true
        }
      }
    },
    "@angular-devkit/core": {
      "version": "13.1.4",
      "resolved": "https://registry.npmjs.org/@angular-devkit/core/-/core-13.1.4.tgz",
      "integrity": "sha512-225Gjy4iVxh5Jo9njJnaG75M/Dt95UW+dEPCGWKV5E/++7UUlXlo9sNWq8x2vJm2nhtsPkpnXNOt4pW1mIDwqQ==",
      "dev": true,
      "requires": {
        "ajv": "8.8.2",
        "ajv-formats": "2.1.1",
        "fast-json-stable-stringify": "2.1.0",
        "magic-string": "0.25.7",
        "rxjs": "6.6.7",
        "source-map": "0.7.3"
      },
      "dependencies": {
        "rxjs": {
          "version": "6.6.7",
          "resolved": "https://registry.npmjs.org/rxjs/-/rxjs-6.6.7.tgz",
          "integrity": "sha512-hTdwr+7yYNIT5n4AMYp85KA6yw2Va0FLa3Rguvbpa4W3I5xynaBZo41cM3XM+4Q6fRMj3sBYIR1VAmZMXYJvRQ==",
          "dev": true,
          "requires": {
            "tslib": "^1.9.0"
          }
        },
        "tslib": {
          "version": "1.14.1",
          "resolved": "https://registry.npmjs.org/tslib/-/tslib-1.14.1.tgz",
          "integrity": "sha512-Xni35NKzjgMrwevysHTCArtLDpPvye8zV/0E4EyYn43P7/7qvQwPh9BGkHewbMulVntbigmcT7rdX3BNo9wRJg==",
          "dev": true
        }
      }
    },
    "@angular-devkit/schematics": {
      "version": "13.1.4",
      "resolved": "https://registry.npmjs.org/@angular-devkit/schematics/-/schematics-13.1.4.tgz",
      "integrity": "sha512-yBa7IeC4cLZ7s137NAQD+sMB5c6SI6UJ6xYxl6J/CvV2RLGOZZA93i4GuRALi5s82eLi1fH+HEL/gvf3JQynzQ==",
      "dev": true,
      "requires": {
        "@angular-devkit/core": "13.1.4",
        "jsonc-parser": "3.0.0",
        "magic-string": "0.25.7",
        "ora": "5.4.1",
        "rxjs": "6.6.7"
      },
      "dependencies": {
        "rxjs": {
          "version": "6.6.7",
          "resolved": "https://registry.npmjs.org/rxjs/-/rxjs-6.6.7.tgz",
          "integrity": "sha512-hTdwr+7yYNIT5n4AMYp85KA6yw2Va0FLa3Rguvbpa4W3I5xynaBZo41cM3XM+4Q6fRMj3sBYIR1VAmZMXYJvRQ==",
          "dev": true,
          "requires": {
            "tslib": "^1.9.0"
          }
        },
        "tslib": {
          "version": "1.14.1",
          "resolved": "https://registry.npmjs.org/tslib/-/tslib-1.14.1.tgz",
          "integrity": "sha512-Xni35NKzjgMrwevysHTCArtLDpPvye8zV/0E4EyYn43P7/7qvQwPh9BGkHewbMulVntbigmcT7rdX3BNo9wRJg==",
          "dev": true
        }
      }
    },
    "@angular/animations": {
      "version": "13.1.3",
      "resolved": "https://registry.npmjs.org/@angular/animations/-/animations-13.1.3.tgz",
      "integrity": "sha512-OwsVQsNHubIgRcxnjti4CU3QJnqd7Z2b+2iu3M349Oxyqxz4DNCqKXalDuJZt/b0yNfirvYO3kCgBfj4PF43QQ==",
      "requires": {
        "tslib": "^2.3.0"
      }
    },
    "@angular/cli": {
      "version": "13.1.4",
      "resolved": "https://registry.npmjs.org/@angular/cli/-/cli-13.1.4.tgz",
      "integrity": "sha512-PP9xpvDDCHhLTIZjewQQzzf+JbpF2s5mXTW2AgIL/E53ukaVvXwwjFMt9dQvECwut/LDpThoc3OfqcGrmwtqnA==",
      "dev": true,
      "requires": {
        "@angular-devkit/architect": "0.1301.4",
        "@angular-devkit/core": "13.1.4",
        "@angular-devkit/schematics": "13.1.4",
        "@schematics/angular": "13.1.4",
        "@yarnpkg/lockfile": "1.1.0",
        "ansi-colors": "4.1.1",
        "debug": "4.3.3",
        "ini": "2.0.0",
        "inquirer": "8.2.0",
        "jsonc-parser": "3.0.0",
        "npm-package-arg": "8.1.5",
        "npm-pick-manifest": "6.1.1",
        "open": "8.4.0",
        "ora": "5.4.1",
        "pacote": "12.0.2",
        "resolve": "1.20.0",
        "semver": "7.3.5",
        "symbol-observable": "4.0.0",
        "uuid": "8.3.2"
      }
    },
    "@angular/common": {
      "version": "13.1.3",
      "resolved": "https://registry.npmjs.org/@angular/common/-/common-13.1.3.tgz",
      "integrity": "sha512-8qf5syeXUogf3+GSu6IRJjrk46UKh9L0QuLx+OSIl/df0y1ewx7e28q3BAUEEnOnKrLzpPNxWs2iwModc4KYfg==",
      "requires": {
        "tslib": "^2.3.0"
      }
    },
    "@angular/compiler": {
      "version": "13.1.3",
      "resolved": "https://registry.npmjs.org/@angular/compiler/-/compiler-13.1.3.tgz",
      "integrity": "sha512-dbHs/Oa+Dn+7i0jKtlVDE0lD0DaUC+lVzAcTK/zS37LrckrTMn1CA+z9bZ4gpHig9RU0wgV3YORxv0wokyiB8A==",
      "requires": {
        "tslib": "^2.3.0"
      }
    },
    "@angular/compiler-cli": {
      "version": "13.1.3",
      "resolved": "https://registry.npmjs.org/@angular/compiler-cli/-/compiler-cli-13.1.3.tgz",
      "integrity": "sha512-ALURaJATc54DzPuiZBvALf/alEp1wr7Hjmw4FuMn2cU7p8lwKkra1Dz5dAZOxh7jAcD1GJfrK/+Sb7A3cuuKjQ==",
      "dev": true,
      "requires": {
        "@babel/core": "^7.8.6",
        "canonical-path": "1.0.0",
        "chokidar": "^3.0.0",
        "convert-source-map": "^1.5.1",
        "dependency-graph": "^0.11.0",
        "magic-string": "^0.25.0",
        "reflect-metadata": "^0.1.2",
        "semver": "^7.0.0",
        "sourcemap-codec": "^1.4.8",
        "tslib": "^2.3.0",
        "yargs": "^17.2.1"
      }
    },
    "@angular/core": {
      "version": "13.1.3",
      "resolved": "https://registry.npmjs.org/@angular/core/-/core-13.1.3.tgz",
      "integrity": "sha512-rvCnIAonRx7VnH2Mv9lQR+UYdlFQQetZCjPw8QOswOspEpHpEPDrp1HxDIqJnHxNqW0n8J3Zev/VgQYr0481UA==",
      "requires": {
        "tslib": "^2.3.0"
      }
    },
    "@angular/forms": {
      "version": "13.1.3",
      "resolved": "https://registry.npmjs.org/@angular/forms/-/forms-13.1.3.tgz",
      "integrity": "sha512-c4N9zZSILyEbomY2CJo1WAMxiHu/qlycvzxKH5NFS2P2+fieORlbKUJ2p1CbYqcIxVnLYRSdWH8f1JpoaG0ETw==",
      "requires": {
        "tslib": "^2.3.0"
      }
    },
    "@angular/platform-browser": {
      "version": "13.1.3",
      "resolved": "https://registry.npmjs.org/@angular/platform-browser/-/platform-browser-13.1.3.tgz",
      "integrity": "sha512-mnWjdr9UTNZvGk8jPI6O9FIhun8Q/0ghy3dg3I9AfRzEG4vPiIZW1ICksTiB+jV9etzhKpidtmg71bwgeXax1A==",
      "requires": {
        "tslib": "^2.3.0"
      }
    },
    "@angular/platform-browser-dynamic": {
      "version": "13.1.3",
      "resolved": "https://registry.npmjs.org/@angular/platform-browser-dynamic/-/platform-browser-dynamic-13.1.3.tgz",
      "integrity": "sha512-vEWyJ+2gkwh2N6KOJfxUNSdSO51ROlzCqqzCfHrPYQrlOFUfKsYKA1uoiB5UGfFEU0HBtIRWn6xoUy3wzVOZbw==",
      "requires": {
        "tslib": "^2.3.0"
      }
    },
    "@angular/router": {
      "version": "13.1.3",
      "resolved": "https://registry.npmjs.org/@angular/router/-/router-13.1.3.tgz",
      "integrity": "sha512-L86kARlc5UNi5KeI0O8PO7wFbTzjEI8ouz+z+aNmCnMUUNX0rbvbuXiPdDvLc71nKZznsPCl2IuO8ojyHrSPsQ==",
      "requires": {
        "tslib": "^2.3.0"
      }
    },
    "@assemblyscript/loader": {
      "version": "0.10.1",
      "resolved": "https://registry.npmjs.org/@assemblyscript/loader/-/loader-0.10.1.tgz",
      "integrity": "sha512-H71nDOOL8Y7kWRLqf6Sums+01Q5msqBW2KhDUTemh1tvY04eSkSXrK0uj/4mmY0Xr16/3zyZmsrxN7CKuRbNRg==",
      "dev": true
    },
    "@babel/code-frame": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/code-frame/-/code-frame-7.16.7.tgz",
      "integrity": "sha512-iAXqUn8IIeBTNd72xsFlgaXHkMBMt6y4HJp1tIaK465CWLT/fG1aqB7ykr95gHHmlBdGbFeWWfyB4NJJ0nmeIg==",
      "dev": true,
      "requires": {
        "@babel/highlight": "^7.16.7"
      }
    },
    "@babel/compat-data": {
      "version": "7.16.8",
      "resolved": "https://registry.npmjs.org/@babel/compat-data/-/compat-data-7.16.8.tgz",
      "integrity": "sha512-m7OkX0IdKLKPpBlJtF561YJal5y/jyI5fNfWbPxh2D/nbzzGI4qRyrD8xO2jB24u7l+5I2a43scCG2IrfjC50Q==",
      "dev": true
    },
    "@babel/core": {
      "version": "7.16.0",
      "resolved": "https://registry.npmjs.org/@babel/core/-/core-7.16.0.tgz",
      "integrity": "sha512-mYZEvshBRHGsIAiyH5PzCFTCfbWfoYbO/jcSdXQSUQu1/pW0xDZAUP7KEc32heqWTAfAHhV9j1vH8Sav7l+JNQ==",
      "dev": true,
      "requires": {
        "@babel/code-frame": "^7.16.0",
        "@babel/generator": "^7.16.0",
        "@babel/helper-compilation-targets": "^7.16.0",
        "@babel/helper-module-transforms": "^7.16.0",
        "@babel/helpers": "^7.16.0",
        "@babel/parser": "^7.16.0",
        "@babel/template": "^7.16.0",
        "@babel/traverse": "^7.16.0",
        "@babel/types": "^7.16.0",
        "convert-source-map": "^1.7.0",
        "debug": "^4.1.0",
        "gensync": "^1.0.0-beta.2",
        "json5": "^2.1.2",
        "semver": "^6.3.0",
        "source-map": "^0.5.0"
      },
      "dependencies": {
        "semver": {
          "version": "6.3.0",
          "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.0.tgz",
          "integrity": "sha512-b39TBaTSfV6yBrapU89p5fKekE2m/NwnDocOVruQFS1/veMgdzuPcnOM34M6CwxW8jH/lxEa5rBoDeUwu5HHTw==",
          "dev": true
        },
        "source-map": {
          "version": "0.5.7",
          "resolved": "https://registry.npmjs.org/source-map/-/source-map-0.5.7.tgz",
          "integrity": "sha1-igOdLRAh0i0eoUyA2OpGi6LvP8w=",
          "dev": true
        }
      }
    },
    "@babel/generator": {
      "version": "7.16.0",
      "resolved": "https://registry.npmjs.org/@babel/generator/-/generator-7.16.0.tgz",
      "integrity": "sha512-RR8hUCfRQn9j9RPKEVXo9LiwoxLPYn6hNZlvUOR8tSnaxlD0p0+la00ZP9/SnRt6HchKr+X0fO2r8vrETiJGew==",
      "dev": true,
      "requires": {
        "@babel/types": "^7.16.0",
        "jsesc": "^2.5.1",
        "source-map": "^0.5.0"
      },
      "dependencies": {
        "source-map": {
          "version": "0.5.7",
          "resolved": "https://registry.npmjs.org/source-map/-/source-map-0.5.7.tgz",
          "integrity": "sha1-igOdLRAh0i0eoUyA2OpGi6LvP8w=",
          "dev": true
        }
      }
    },
    "@babel/helper-annotate-as-pure": {
      "version": "7.16.0",
      "resolved": "https://registry.npmjs.org/@babel/helper-annotate-as-pure/-/helper-annotate-as-pure-7.16.0.tgz",
      "integrity": "sha512-ItmYF9vR4zA8cByDocY05o0LGUkp1zhbTQOH1NFyl5xXEqlTJQCEJjieriw+aFpxo16swMxUnUiKS7a/r4vtHg==",
      "dev": true,
      "requires": {
        "@babel/types": "^7.16.0"
      }
    },
    "@babel/helper-builder-binary-assignment-operator-visitor": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-builder-binary-assignment-operator-visitor/-/helper-builder-binary-assignment-operator-visitor-7.16.7.tgz",
      "integrity": "sha512-C6FdbRaxYjwVu/geKW4ZeQ0Q31AftgRcdSnZ5/jsH6BzCJbtvXvhpfkbkThYSuutZA7nCXpPR6AD9zd1dprMkA==",
      "dev": true,
      "requires": {
        "@babel/helper-explode-assignable-expression": "^7.16.7",
        "@babel/types": "^7.16.7"
      }
    },
    "@babel/helper-compilation-targets": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-compilation-targets/-/helper-compilation-targets-7.16.7.tgz",
      "integrity": "sha512-mGojBwIWcwGD6rfqgRXVlVYmPAv7eOpIemUG3dGnDdCY4Pae70ROij3XmfrH6Fa1h1aiDylpglbZyktfzyo/hA==",
      "dev": true,
      "requires": {
        "@babel/compat-data": "^7.16.4",
        "@babel/helper-validator-option": "^7.16.7",
        "browserslist": "^4.17.5",
        "semver": "^6.3.0"
      },
      "dependencies": {
        "semver": {
          "version": "6.3.0",
          "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.0.tgz",
          "integrity": "sha512-b39TBaTSfV6yBrapU89p5fKekE2m/NwnDocOVruQFS1/veMgdzuPcnOM34M6CwxW8jH/lxEa5rBoDeUwu5HHTw==",
          "dev": true
        }
      }
    },
    "@babel/helper-create-class-features-plugin": {
      "version": "7.16.10",
      "resolved": "https://registry.npmjs.org/@babel/helper-create-class-features-plugin/-/helper-create-class-features-plugin-7.16.10.tgz",
      "integrity": "sha512-wDeej0pu3WN/ffTxMNCPW5UCiOav8IcLRxSIyp/9+IF2xJUM9h/OYjg0IJLHaL6F8oU8kqMz9nc1vryXhMsgXg==",
      "dev": true,
      "requires": {
        "@babel/helper-annotate-as-pure": "^7.16.7",
        "@babel/helper-environment-visitor": "^7.16.7",
        "@babel/helper-function-name": "^7.16.7",
        "@babel/helper-member-expression-to-functions": "^7.16.7",
        "@babel/helper-optimise-call-expression": "^7.16.7",
        "@babel/helper-replace-supers": "^7.16.7",
        "@babel/helper-split-export-declaration": "^7.16.7"
      },
      "dependencies": {
        "@babel/helper-annotate-as-pure": {
          "version": "7.16.7",
          "resolved": "https://registry.npmjs.org/@babel/helper-annotate-as-pure/-/helper-annotate-as-pure-7.16.7.tgz",
          "integrity": "sha512-s6t2w/IPQVTAET1HitoowRGXooX8mCgtuP5195wD/QJPV6wYjpujCGF7JuMODVX2ZAJOf1GT6DT9MHEZvLOFSw==",
          "dev": true,
          "requires": {
            "@babel/types": "^7.16.7"
          }
        }
      }
    },
    "@babel/helper-create-regexp-features-plugin": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-create-regexp-features-plugin/-/helper-create-regexp-features-plugin-7.16.7.tgz",
      "integrity": "sha512-fk5A6ymfp+O5+p2yCkXAu5Kyj6v0xh0RBeNcAkYUMDvvAAoxvSKXn+Jb37t/yWFiQVDFK1ELpUTD8/aLhCPu+g==",
      "dev": true,
      "requires": {
        "@babel/helper-annotate-as-pure": "^7.16.7",
        "regexpu-core": "^4.7.1"
      },
      "dependencies": {
        "@babel/helper-annotate-as-pure": {
          "version": "7.16.7",
          "resolved": "https://registry.npmjs.org/@babel/helper-annotate-as-pure/-/helper-annotate-as-pure-7.16.7.tgz",
          "integrity": "sha512-s6t2w/IPQVTAET1HitoowRGXooX8mCgtuP5195wD/QJPV6wYjpujCGF7JuMODVX2ZAJOf1GT6DT9MHEZvLOFSw==",
          "dev": true,
          "requires": {
            "@babel/types": "^7.16.7"
          }
        }
      }
    },
    "@babel/helper-define-polyfill-provider": {
      "version": "0.3.1",
      "resolved": "https://registry.npmjs.org/@babel/helper-define-polyfill-provider/-/helper-define-polyfill-provider-0.3.1.tgz",
      "integrity": "sha512-J9hGMpJQmtWmj46B3kBHmL38UhJGhYX7eqkcq+2gsstyYt341HmPeWspihX43yVRA0mS+8GGk2Gckc7bY/HCmA==",
      "dev": true,
      "requires": {
        "@babel/helper-compilation-targets": "^7.13.0",
        "@babel/helper-module-imports": "^7.12.13",
        "@babel/helper-plugin-utils": "^7.13.0",
        "@babel/traverse": "^7.13.0",
        "debug": "^4.1.1",
        "lodash.debounce": "^4.0.8",
        "resolve": "^1.14.2",
        "semver": "^6.1.2"
      },
      "dependencies": {
        "semver": {
          "version": "6.3.0",
          "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.0.tgz",
          "integrity": "sha512-b39TBaTSfV6yBrapU89p5fKekE2m/NwnDocOVruQFS1/veMgdzuPcnOM34M6CwxW8jH/lxEa5rBoDeUwu5HHTw==",
          "dev": true
        }
      }
    },
    "@babel/helper-environment-visitor": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-environment-visitor/-/helper-environment-visitor-7.16.7.tgz",
      "integrity": "sha512-SLLb0AAn6PkUeAfKJCCOl9e1R53pQlGAfc4y4XuMRZfqeMYLE0dM1LMhqbGAlGQY0lfw5/ohoYWAe9V1yibRag==",
      "dev": true,
      "requires": {
        "@babel/types": "^7.16.7"
      }
    },
    "@babel/helper-explode-assignable-expression": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-explode-assignable-expression/-/helper-explode-assignable-expression-7.16.7.tgz",
      "integrity": "sha512-KyUenhWMC8VrxzkGP0Jizjo4/Zx+1nNZhgocs+gLzyZyB8SHidhoq9KK/8Ato4anhwsivfkBLftky7gvzbZMtQ==",
      "dev": true,
      "requires": {
        "@babel/types": "^7.16.7"
      }
    },
    "@babel/helper-function-name": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-function-name/-/helper-function-name-7.16.7.tgz",
      "integrity": "sha512-QfDfEnIUyyBSR3HtrtGECuZ6DAyCkYFp7GHl75vFtTnn6pjKeK0T1DB5lLkFvBea8MdaiUABx3osbgLyInoejA==",
      "dev": true,
      "requires": {
        "@babel/helper-get-function-arity": "^7.16.7",
        "@babel/template": "^7.16.7",
        "@babel/types": "^7.16.7"
      },
      "dependencies": {
        "@babel/template": {
          "version": "7.16.7",
          "resolved": "https://registry.npmjs.org/@babel/template/-/template-7.16.7.tgz",
          "integrity": "sha512-I8j/x8kHUrbYRTUxXrrMbfCa7jxkE7tZre39x3kjr9hvI82cK1FfqLygotcWN5kdPGWcLdWMHpSBavse5tWw3w==",
          "dev": true,
          "requires": {
            "@babel/code-frame": "^7.16.7",
            "@babel/parser": "^7.16.7",
            "@babel/types": "^7.16.7"
          }
        }
      }
    },
    "@babel/helper-get-function-arity": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-get-function-arity/-/helper-get-function-arity-7.16.7.tgz",
      "integrity": "sha512-flc+RLSOBXzNzVhcLu6ujeHUrD6tANAOU5ojrRx/as+tbzf8+stUCj7+IfRRoAbEZqj/ahXEMsjhOhgeZsrnTw==",
      "dev": true,
      "requires": {
        "@babel/types": "^7.16.7"
      }
    },
    "@babel/helper-hoist-variables": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-hoist-variables/-/helper-hoist-variables-7.16.7.tgz",
      "integrity": "sha512-m04d/0Op34H5v7pbZw6pSKP7weA6lsMvfiIAMeIvkY/R4xQtBSMFEigu9QTZ2qB/9l22vsxtM8a+Q8CzD255fg==",
      "dev": true,
      "requires": {
        "@babel/types": "^7.16.7"
      }
    },
    "@babel/helper-member-expression-to-functions": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-member-expression-to-functions/-/helper-member-expression-to-functions-7.16.7.tgz",
      "integrity": "sha512-VtJ/65tYiU/6AbMTDwyoXGPKHgTsfRarivm+YbB5uAzKUyuPjgZSgAFeG87FCigc7KNHu2Pegh1XIT3lXjvz3Q==",
      "dev": true,
      "requires": {
        "@babel/types": "^7.16.7"
      }
    },
    "@babel/helper-module-imports": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-module-imports/-/helper-module-imports-7.16.7.tgz",
      "integrity": "sha512-LVtS6TqjJHFc+nYeITRo6VLXve70xmq7wPhWTqDJusJEgGmkAACWwMiTNrvfoQo6hEhFwAIixNkvB0jPXDL8Wg==",
      "dev": true,
      "requires": {
        "@babel/types": "^7.16.7"
      }
    },
    "@babel/helper-module-transforms": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-module-transforms/-/helper-module-transforms-7.16.7.tgz",
      "integrity": "sha512-gaqtLDxJEFCeQbYp9aLAefjhkKdjKcdh6DB7jniIGU3Pz52WAmP268zK0VgPz9hUNkMSYeH976K2/Y6yPadpng==",
      "dev": true,
      "requires": {
        "@babel/helper-environment-visitor": "^7.16.7",
        "@babel/helper-module-imports": "^7.16.7",
        "@babel/helper-simple-access": "^7.16.7",
        "@babel/helper-split-export-declaration": "^7.16.7",
        "@babel/helper-validator-identifier": "^7.16.7",
        "@babel/template": "^7.16.7",
        "@babel/traverse": "^7.16.7",
        "@babel/types": "^7.16.7"
      },
      "dependencies": {
        "@babel/template": {
          "version": "7.16.7",
          "resolved": "https://registry.npmjs.org/@babel/template/-/template-7.16.7.tgz",
          "integrity": "sha512-I8j/x8kHUrbYRTUxXrrMbfCa7jxkE7tZre39x3kjr9hvI82cK1FfqLygotcWN5kdPGWcLdWMHpSBavse5tWw3w==",
          "dev": true,
          "requires": {
            "@babel/code-frame": "^7.16.7",
            "@babel/parser": "^7.16.7",
            "@babel/types": "^7.16.7"
          }
        }
      }
    },
    "@babel/helper-optimise-call-expression": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-optimise-call-expression/-/helper-optimise-call-expression-7.16.7.tgz",
      "integrity": "sha512-EtgBhg7rd/JcnpZFXpBy0ze1YRfdm7BnBX4uKMBd3ixa3RGAE002JZB66FJyNH7g0F38U05pXmA5P8cBh7z+1w==",
      "dev": true,
      "requires": {
        "@babel/types": "^7.16.7"
      }
    },
    "@babel/helper-plugin-utils": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-plugin-utils/-/helper-plugin-utils-7.16.7.tgz",
      "integrity": "sha512-Qg3Nk7ZxpgMrsox6HreY1ZNKdBq7K72tDSliA6dCl5f007jR4ne8iD5UzuNnCJH2xBf2BEEVGr+/OL6Gdp7RxA==",
      "dev": true
    },
    "@babel/helper-remap-async-to-generator": {
      "version": "7.16.8",
      "resolved": "https://registry.npmjs.org/@babel/helper-remap-async-to-generator/-/helper-remap-async-to-generator-7.16.8.tgz",
      "integrity": "sha512-fm0gH7Flb8H51LqJHy3HJ3wnE1+qtYR2A99K06ahwrawLdOFsCEWjZOrYricXJHoPSudNKxrMBUPEIPxiIIvBw==",
      "dev": true,
      "requires": {
        "@babel/helper-annotate-as-pure": "^7.16.7",
        "@babel/helper-wrap-function": "^7.16.8",
        "@babel/types": "^7.16.8"
      },
      "dependencies": {
        "@babel/helper-annotate-as-pure": {
          "version": "7.16.7",
          "resolved": "https://registry.npmjs.org/@babel/helper-annotate-as-pure/-/helper-annotate-as-pure-7.16.7.tgz",
          "integrity": "sha512-s6t2w/IPQVTAET1HitoowRGXooX8mCgtuP5195wD/QJPV6wYjpujCGF7JuMODVX2ZAJOf1GT6DT9MHEZvLOFSw==",
          "dev": true,
          "requires": {
            "@babel/types": "^7.16.7"
          }
        }
      }
    },
    "@babel/helper-replace-supers": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-replace-supers/-/helper-replace-supers-7.16.7.tgz",
      "integrity": "sha512-y9vsWilTNaVnVh6xiJfABzsNpgDPKev9HnAgz6Gb1p6UUwf9NepdlsV7VXGCftJM+jqD5f7JIEubcpLjZj5dBw==",
      "dev": true,
      "requires": {
        "@babel/helper-environment-visitor": "^7.16.7",
        "@babel/helper-member-expression-to-functions": "^7.16.7",
        "@babel/helper-optimise-call-expression": "^7.16.7",
        "@babel/traverse": "^7.16.7",
        "@babel/types": "^7.16.7"
      }
    },
    "@babel/helper-simple-access": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-simple-access/-/helper-simple-access-7.16.7.tgz",
      "integrity": "sha512-ZIzHVyoeLMvXMN/vok/a4LWRy8G2v205mNP0XOuf9XRLyX5/u9CnVulUtDgUTama3lT+bf/UqucuZjqiGuTS1g==",
      "dev": true,
      "requires": {
        "@babel/types": "^7.16.7"
      }
    },
    "@babel/helper-skip-transparent-expression-wrappers": {
      "version": "7.16.0",
      "resolved": "https://registry.npmjs.org/@babel/helper-skip-transparent-expression-wrappers/-/helper-skip-transparent-expression-wrappers-7.16.0.tgz",
      "integrity": "sha512-+il1gTy0oHwUsBQZyJvukbB4vPMdcYBrFHa0Uc4AizLxbq6BOYC51Rv4tWocX9BLBDLZ4kc6qUFpQ6HRgL+3zw==",
      "dev": true,
      "requires": {
        "@babel/types": "^7.16.0"
      }
    },
    "@babel/helper-split-export-declaration": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-split-export-declaration/-/helper-split-export-declaration-7.16.7.tgz",
      "integrity": "sha512-xbWoy/PFoxSWazIToT9Sif+jJTlrMcndIsaOKvTA6u7QEo7ilkRZpjew18/W3c7nm8fXdUDXh02VXTbZ0pGDNw==",
      "dev": true,
      "requires": {
        "@babel/types": "^7.16.7"
      }
    },
    "@babel/helper-validator-identifier": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-validator-identifier/-/helper-validator-identifier-7.16.7.tgz",
      "integrity": "sha512-hsEnFemeiW4D08A5gUAZxLBTXpZ39P+a+DGDsHw1yxqyQ/jzFEnxf5uTEGp+3bzAbNOxU1paTgYS4ECU/IgfDw==",
      "dev": true
    },
    "@babel/helper-validator-option": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helper-validator-option/-/helper-validator-option-7.16.7.tgz",
      "integrity": "sha512-TRtenOuRUVo9oIQGPC5G9DgK4743cdxvtOw0weQNpZXaS16SCBi5MNjZF8vba3ETURjZpTbVn7Vvcf2eAwFozQ==",
      "dev": true
    },
    "@babel/helper-wrap-function": {
      "version": "7.16.8",
      "resolved": "https://registry.npmjs.org/@babel/helper-wrap-function/-/helper-wrap-function-7.16.8.tgz",
      "integrity": "sha512-8RpyRVIAW1RcDDGTA+GpPAwV22wXCfKOoM9bet6TLkGIFTkRQSkH1nMQ5Yet4MpoXe1ZwHPVtNasc2w0uZMqnw==",
      "dev": true,
      "requires": {
        "@babel/helper-function-name": "^7.16.7",
        "@babel/template": "^7.16.7",
        "@babel/traverse": "^7.16.8",
        "@babel/types": "^7.16.8"
      },
      "dependencies": {
        "@babel/template": {
          "version": "7.16.7",
          "resolved": "https://registry.npmjs.org/@babel/template/-/template-7.16.7.tgz",
          "integrity": "sha512-I8j/x8kHUrbYRTUxXrrMbfCa7jxkE7tZre39x3kjr9hvI82cK1FfqLygotcWN5kdPGWcLdWMHpSBavse5tWw3w==",
          "dev": true,
          "requires": {
            "@babel/code-frame": "^7.16.7",
            "@babel/parser": "^7.16.7",
            "@babel/types": "^7.16.7"
          }
        }
      }
    },
    "@babel/helpers": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/helpers/-/helpers-7.16.7.tgz",
      "integrity": "sha512-9ZDoqtfY7AuEOt3cxchfii6C7GDyyMBffktR5B2jvWv8u2+efwvpnVKXMWzNehqy68tKgAfSwfdw/lWpthS2bw==",
      "dev": true,
      "requires": {
        "@babel/template": "^7.16.7",
        "@babel/traverse": "^7.16.7",
        "@babel/types": "^7.16.7"
      },
      "dependencies": {
        "@babel/template": {
          "version": "7.16.7",
          "resolved": "https://registry.npmjs.org/@babel/template/-/template-7.16.7.tgz",
          "integrity": "sha512-I8j/x8kHUrbYRTUxXrrMbfCa7jxkE7tZre39x3kjr9hvI82cK1FfqLygotcWN5kdPGWcLdWMHpSBavse5tWw3w==",
          "dev": true,
          "requires": {
            "@babel/code-frame": "^7.16.7",
            "@babel/parser": "^7.16.7",
            "@babel/types": "^7.16.7"
          }
        }
      }
    },
    "@babel/highlight": {
      "version": "7.16.10",
      "resolved": "https://registry.npmjs.org/@babel/highlight/-/highlight-7.16.10.tgz",
      "integrity": "sha512-5FnTQLSLswEj6IkgVw5KusNUUFY9ZGqe/TRFnP/BKYHYgfh7tc+C7mwiy95/yNP7Dh9x580Vv8r7u7ZfTBFxdw==",
      "dev": true,
      "requires": {
        "@babel/helper-validator-identifier": "^7.16.7",
        "chalk": "^2.0.0",
        "js-tokens": "^4.0.0"
      }
    },
    "@babel/parser": {
      "version": "7.16.12",
      "resolved": "https://registry.npmjs.org/@babel/parser/-/parser-7.16.12.tgz",
      "integrity": "sha512-VfaV15po8RiZssrkPweyvbGVSe4x2y+aciFCgn0n0/SJMR22cwofRV1mtnJQYcSB1wUTaA/X1LnA3es66MCO5A==",
      "dev": true
    },
    "@babel/plugin-bugfix-safari-id-destructuring-collision-in-function-expression": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-bugfix-safari-id-destructuring-collision-in-function-expression/-/plugin-bugfix-safari-id-destructuring-collision-in-function-expression-7.16.7.tgz",
      "integrity": "sha512-anv/DObl7waiGEnC24O9zqL0pSuI9hljihqiDuFHC8d7/bjr/4RLGPWuc8rYOff/QPzbEPSkzG8wGG9aDuhHRg==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-bugfix-v8-spread-parameters-in-optional-chaining": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-bugfix-v8-spread-parameters-in-optional-chaining/-/plugin-bugfix-v8-spread-parameters-in-optional-chaining-7.16.7.tgz",
      "integrity": "sha512-di8vUHRdf+4aJ7ltXhaDbPoszdkh59AQtJM5soLsuHpQJdFQZOA4uGj0V2u/CZ8bJ/u8ULDL5yq6FO/bCXnKHw==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/helper-skip-transparent-expression-wrappers": "^7.16.0",
        "@babel/plugin-proposal-optional-chaining": "^7.16.7"
      }
    },
    "@babel/plugin-proposal-async-generator-functions": {
      "version": "7.16.4",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-async-generator-functions/-/plugin-proposal-async-generator-functions-7.16.4.tgz",
      "integrity": "sha512-/CUekqaAaZCQHleSK/9HajvcD/zdnJiKRiuUFq8ITE+0HsPzquf53cpFiqAwl/UfmJbR6n5uGPQSPdrmKOvHHg==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.14.5",
        "@babel/helper-remap-async-to-generator": "^7.16.4",
        "@babel/plugin-syntax-async-generators": "^7.8.4"
      }
    },
    "@babel/plugin-proposal-class-properties": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-class-properties/-/plugin-proposal-class-properties-7.16.7.tgz",
      "integrity": "sha512-IobU0Xme31ewjYOShSIqd/ZGM/r/cuOz2z0MDbNrhF5FW+ZVgi0f2lyeoj9KFPDOAqsYxmLWZte1WOwlvY9aww==",
      "dev": true,
      "requires": {
        "@babel/helper-create-class-features-plugin": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-proposal-class-static-block": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-class-static-block/-/plugin-proposal-class-static-block-7.16.7.tgz",
      "integrity": "sha512-dgqJJrcZoG/4CkMopzhPJjGxsIe9A8RlkQLnL/Vhhx8AA9ZuaRwGSlscSh42hazc7WSrya/IK7mTeoF0DP9tEw==",
      "dev": true,
      "requires": {
        "@babel/helper-create-class-features-plugin": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/plugin-syntax-class-static-block": "^7.14.5"
      }
    },
    "@babel/plugin-proposal-dynamic-import": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-dynamic-import/-/plugin-proposal-dynamic-import-7.16.7.tgz",
      "integrity": "sha512-I8SW9Ho3/8DRSdmDdH3gORdyUuYnk1m4cMxUAdu5oy4n3OfN8flDEH+d60iG7dUfi0KkYwSvoalHzzdRzpWHTg==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/plugin-syntax-dynamic-import": "^7.8.3"
      }
    },
    "@babel/plugin-proposal-export-namespace-from": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-export-namespace-from/-/plugin-proposal-export-namespace-from-7.16.7.tgz",
      "integrity": "sha512-ZxdtqDXLRGBL64ocZcs7ovt71L3jhC1RGSyR996svrCi3PYqHNkb3SwPJCs8RIzD86s+WPpt2S73+EHCGO+NUA==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/plugin-syntax-export-namespace-from": "^7.8.3"
      }
    },
    "@babel/plugin-proposal-json-strings": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-json-strings/-/plugin-proposal-json-strings-7.16.7.tgz",
      "integrity": "sha512-lNZ3EEggsGY78JavgbHsK9u5P3pQaW7k4axlgFLYkMd7UBsiNahCITShLjNQschPyjtO6dADrL24757IdhBrsQ==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/plugin-syntax-json-strings": "^7.8.3"
      }
    },
    "@babel/plugin-proposal-logical-assignment-operators": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-logical-assignment-operators/-/plugin-proposal-logical-assignment-operators-7.16.7.tgz",
      "integrity": "sha512-K3XzyZJGQCr00+EtYtrDjmwX7o7PLK6U9bi1nCwkQioRFVUv6dJoxbQjtWVtP+bCPy82bONBKG8NPyQ4+i6yjg==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/plugin-syntax-logical-assignment-operators": "^7.10.4"
      }
    },
    "@babel/plugin-proposal-nullish-coalescing-operator": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-nullish-coalescing-operator/-/plugin-proposal-nullish-coalescing-operator-7.16.7.tgz",
      "integrity": "sha512-aUOrYU3EVtjf62jQrCj63pYZ7k6vns2h/DQvHPWGmsJRYzWXZ6/AsfgpiRy6XiuIDADhJzP2Q9MwSMKauBQ+UQ==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/plugin-syntax-nullish-coalescing-operator": "^7.8.3"
      }
    },
    "@babel/plugin-proposal-numeric-separator": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-numeric-separator/-/plugin-proposal-numeric-separator-7.16.7.tgz",
      "integrity": "sha512-vQgPMknOIgiuVqbokToyXbkY/OmmjAzr/0lhSIbG/KmnzXPGwW/AdhdKpi+O4X/VkWiWjnkKOBiqJrTaC98VKw==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/plugin-syntax-numeric-separator": "^7.10.4"
      }
    },
    "@babel/plugin-proposal-object-rest-spread": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-object-rest-spread/-/plugin-proposal-object-rest-spread-7.16.7.tgz",
      "integrity": "sha512-3O0Y4+dw94HA86qSg9IHfyPktgR7q3gpNVAeiKQd+8jBKFaU5NQS1Yatgo4wY+UFNuLjvxcSmzcsHqrhgTyBUA==",
      "dev": true,
      "requires": {
        "@babel/compat-data": "^7.16.4",
        "@babel/helper-compilation-targets": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/plugin-syntax-object-rest-spread": "^7.8.3",
        "@babel/plugin-transform-parameters": "^7.16.7"
      }
    },
    "@babel/plugin-proposal-optional-catch-binding": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-optional-catch-binding/-/plugin-proposal-optional-catch-binding-7.16.7.tgz",
      "integrity": "sha512-eMOH/L4OvWSZAE1VkHbr1vckLG1WUcHGJSLqqQwl2GaUqG6QjddvrOaTUMNYiv77H5IKPMZ9U9P7EaHwvAShfA==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/plugin-syntax-optional-catch-binding": "^7.8.3"
      }
    },
    "@babel/plugin-proposal-optional-chaining": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-optional-chaining/-/plugin-proposal-optional-chaining-7.16.7.tgz",
      "integrity": "sha512-eC3xy+ZrUcBtP7x+sq62Q/HYd674pPTb/77XZMb5wbDPGWIdUbSr4Agr052+zaUPSb+gGRnjxXfKFvx5iMJ+DA==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/helper-skip-transparent-expression-wrappers": "^7.16.0",
        "@babel/plugin-syntax-optional-chaining": "^7.8.3"
      }
    },
    "@babel/plugin-proposal-private-methods": {
      "version": "7.16.11",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-private-methods/-/plugin-proposal-private-methods-7.16.11.tgz",
      "integrity": "sha512-F/2uAkPlXDr8+BHpZvo19w3hLFKge+k75XUprE6jaqKxjGkSYcK+4c+bup5PdW/7W/Rpjwql7FTVEDW+fRAQsw==",
      "dev": true,
      "requires": {
        "@babel/helper-create-class-features-plugin": "^7.16.10",
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-proposal-private-property-in-object": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-private-property-in-object/-/plugin-proposal-private-property-in-object-7.16.7.tgz",
      "integrity": "sha512-rMQkjcOFbm+ufe3bTZLyOfsOUOxyvLXZJCTARhJr+8UMSoZmqTe1K1BgkFcrW37rAchWg57yI69ORxiWvUINuQ==",
      "dev": true,
      "requires": {
        "@babel/helper-annotate-as-pure": "^7.16.7",
        "@babel/helper-create-class-features-plugin": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/plugin-syntax-private-property-in-object": "^7.14.5"
      },
      "dependencies": {
        "@babel/helper-annotate-as-pure": {
          "version": "7.16.7",
          "resolved": "https://registry.npmjs.org/@babel/helper-annotate-as-pure/-/helper-annotate-as-pure-7.16.7.tgz",
          "integrity": "sha512-s6t2w/IPQVTAET1HitoowRGXooX8mCgtuP5195wD/QJPV6wYjpujCGF7JuMODVX2ZAJOf1GT6DT9MHEZvLOFSw==",
          "dev": true,
          "requires": {
            "@babel/types": "^7.16.7"
          }
        }
      }
    },
    "@babel/plugin-proposal-unicode-property-regex": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-proposal-unicode-property-regex/-/plugin-proposal-unicode-property-regex-7.16.7.tgz",
      "integrity": "sha512-QRK0YI/40VLhNVGIjRNAAQkEHws0cswSdFFjpFyt943YmJIU1da9uW63Iu6NFV6CxTZW5eTDCrwZUstBWgp/Rg==",
      "dev": true,
      "requires": {
        "@babel/helper-create-regexp-features-plugin": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-syntax-async-generators": {
      "version": "7.8.4",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-async-generators/-/plugin-syntax-async-generators-7.8.4.tgz",
      "integrity": "sha512-tycmZxkGfZaxhMRbXlPXuVFpdWlXpir2W4AMhSJgRKzk/eDlIXOhb2LHWoLpDF7TEHylV5zNhykX6KAgHJmTNw==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.8.0"
      }
    },
    "@babel/plugin-syntax-class-properties": {
      "version": "7.12.13",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-class-properties/-/plugin-syntax-class-properties-7.12.13.tgz",
      "integrity": "sha512-fm4idjKla0YahUNgFNLCB0qySdsoPiZP3iQE3rky0mBUtMZ23yDJ9SJdg6dXTSDnulOVqiF3Hgr9nbXvXTQZYA==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.12.13"
      }
    },
    "@babel/plugin-syntax-class-static-block": {
      "version": "7.14.5",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-class-static-block/-/plugin-syntax-class-static-block-7.14.5.tgz",
      "integrity": "sha512-b+YyPmr6ldyNnM6sqYeMWE+bgJcJpO6yS4QD7ymxgH34GBPNDM/THBh8iunyvKIZztiwLH4CJZ0RxTk9emgpjw==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.14.5"
      }
    },
    "@babel/plugin-syntax-dynamic-import": {
      "version": "7.8.3",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-dynamic-import/-/plugin-syntax-dynamic-import-7.8.3.tgz",
      "integrity": "sha512-5gdGbFon+PszYzqs83S3E5mpi7/y/8M9eC90MRTZfduQOYW76ig6SOSPNe41IG5LoP3FGBn2N0RjVDSQiS94kQ==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.8.0"
      }
    },
    "@babel/plugin-syntax-export-namespace-from": {
      "version": "7.8.3",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-export-namespace-from/-/plugin-syntax-export-namespace-from-7.8.3.tgz",
      "integrity": "sha512-MXf5laXo6c1IbEbegDmzGPwGNTsHZmEy6QGznu5Sh2UCWvueywb2ee+CCE4zQiZstxU9BMoQO9i6zUFSY0Kj0Q==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.8.3"
      }
    },
    "@babel/plugin-syntax-json-strings": {
      "version": "7.8.3",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-json-strings/-/plugin-syntax-json-strings-7.8.3.tgz",
      "integrity": "sha512-lY6kdGpWHvjoe2vk4WrAapEuBR69EMxZl+RoGRhrFGNYVK8mOPAW8VfbT/ZgrFbXlDNiiaxQnAtgVCZ6jv30EA==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.8.0"
      }
    },
    "@babel/plugin-syntax-logical-assignment-operators": {
      "version": "7.10.4",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-logical-assignment-operators/-/plugin-syntax-logical-assignment-operators-7.10.4.tgz",
      "integrity": "sha512-d8waShlpFDinQ5MtvGU9xDAOzKH47+FFoney2baFIoMr952hKOLp1HR7VszoZvOsV/4+RRszNY7D17ba0te0ig==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.10.4"
      }
    },
    "@babel/plugin-syntax-nullish-coalescing-operator": {
      "version": "7.8.3",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-nullish-coalescing-operator/-/plugin-syntax-nullish-coalescing-operator-7.8.3.tgz",
      "integrity": "sha512-aSff4zPII1u2QD7y+F8oDsz19ew4IGEJg9SVW+bqwpwtfFleiQDMdzA/R+UlWDzfnHFCxxleFT0PMIrR36XLNQ==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.8.0"
      }
    },
    "@babel/plugin-syntax-numeric-separator": {
      "version": "7.10.4",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-numeric-separator/-/plugin-syntax-numeric-separator-7.10.4.tgz",
      "integrity": "sha512-9H6YdfkcK/uOnY/K7/aA2xpzaAgkQn37yzWUMRK7OaPOqOpGS1+n0H5hxT9AUw9EsSjPW8SVyMJwYRtWs3X3ug==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.10.4"
      }
    },
    "@babel/plugin-syntax-object-rest-spread": {
      "version": "7.8.3",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-object-rest-spread/-/plugin-syntax-object-rest-spread-7.8.3.tgz",
      "integrity": "sha512-XoqMijGZb9y3y2XskN+P1wUGiVwWZ5JmoDRwx5+3GmEplNyVM2s2Dg8ILFQm8rWM48orGy5YpI5Bl8U1y7ydlA==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.8.0"
      }
    },
    "@babel/plugin-syntax-optional-catch-binding": {
      "version": "7.8.3",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-optional-catch-binding/-/plugin-syntax-optional-catch-binding-7.8.3.tgz",
      "integrity": "sha512-6VPD0Pc1lpTqw0aKoeRTMiB+kWhAoT24PA+ksWSBrFtl5SIRVpZlwN3NNPQjehA2E/91FV3RjLWoVTglWcSV3Q==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.8.0"
      }
    },
    "@babel/plugin-syntax-optional-chaining": {
      "version": "7.8.3",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-optional-chaining/-/plugin-syntax-optional-chaining-7.8.3.tgz",
      "integrity": "sha512-KoK9ErH1MBlCPxV0VANkXW2/dw4vlbGDrFgz8bmUsBGYkFRcbRwMh6cIJubdPrkxRwuGdtCk0v/wPTKbQgBjkg==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.8.0"
      }
    },
    "@babel/plugin-syntax-private-property-in-object": {
      "version": "7.14.5",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-private-property-in-object/-/plugin-syntax-private-property-in-object-7.14.5.tgz",
      "integrity": "sha512-0wVnp9dxJ72ZUJDV27ZfbSj6iHLoytYZmh3rFcxNnvsJF3ktkzLDZPy/mA17HGsaQT3/DQsWYX1f1QGWkCoVUg==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.14.5"
      }
    },
    "@babel/plugin-syntax-top-level-await": {
      "version": "7.14.5",
      "resolved": "https://registry.npmjs.org/@babel/plugin-syntax-top-level-await/-/plugin-syntax-top-level-await-7.14.5.tgz",
      "integrity": "sha512-hx++upLv5U1rgYfwe1xBQUhRmU41NEvpUvrp8jkrSCdvGSnM5/qdRMtylJ6PG5OFkBaHkbTAKTnd3/YyESRHFw==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.14.5"
      }
    },
    "@babel/plugin-transform-arrow-functions": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-arrow-functions/-/plugin-transform-arrow-functions-7.16.7.tgz",
      "integrity": "sha512-9ffkFFMbvzTvv+7dTp/66xvZAWASuPD5Tl9LK3Z9vhOmANo6j94rik+5YMBt4CwHVMWLWpMsriIc2zsa3WW3xQ==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-transform-async-to-generator": {
      "version": "7.16.0",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-async-to-generator/-/plugin-transform-async-to-generator-7.16.0.tgz",
      "integrity": "sha512-PbIr7G9kR8tdH6g8Wouir5uVjklETk91GMVSUq+VaOgiinbCkBP6Q7NN/suM/QutZkMJMvcyAriogcYAdhg8Gw==",
      "dev": true,
      "requires": {
        "@babel/helper-module-imports": "^7.16.0",
        "@babel/helper-plugin-utils": "^7.14.5",
        "@babel/helper-remap-async-to-generator": "^7.16.0"
      }
    },
    "@babel/plugin-transform-block-scoped-functions": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-block-scoped-functions/-/plugin-transform-block-scoped-functions-7.16.7.tgz",
      "integrity": "sha512-JUuzlzmF40Z9cXyytcbZEZKckgrQzChbQJw/5PuEHYeqzCsvebDx0K0jWnIIVcmmDOAVctCgnYs0pMcrYj2zJg==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-transform-block-scoping": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-block-scoping/-/plugin-transform-block-scoping-7.16.7.tgz",
      "integrity": "sha512-ObZev2nxVAYA4bhyusELdo9hb3H+A56bxH3FZMbEImZFiEDYVHXQSJ1hQKFlDnlt8G9bBrCZ5ZpURZUrV4G5qQ==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-transform-classes": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-classes/-/plugin-transform-classes-7.16.7.tgz",
      "integrity": "sha512-WY7og38SFAGYRe64BrjKf8OrE6ulEHtr5jEYaZMwox9KebgqPi67Zqz8K53EKk1fFEJgm96r32rkKZ3qA2nCWQ==",
      "dev": true,
      "requires": {
        "@babel/helper-annotate-as-pure": "^7.16.7",
        "@babel/helper-environment-visitor": "^7.16.7",
        "@babel/helper-function-name": "^7.16.7",
        "@babel/helper-optimise-call-expression": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/helper-replace-supers": "^7.16.7",
        "@babel/helper-split-export-declaration": "^7.16.7",
        "globals": "^11.1.0"
      },
      "dependencies": {
        "@babel/helper-annotate-as-pure": {
          "version": "7.16.7",
          "resolved": "https://registry.npmjs.org/@babel/helper-annotate-as-pure/-/helper-annotate-as-pure-7.16.7.tgz",
          "integrity": "sha512-s6t2w/IPQVTAET1HitoowRGXooX8mCgtuP5195wD/QJPV6wYjpujCGF7JuMODVX2ZAJOf1GT6DT9MHEZvLOFSw==",
          "dev": true,
          "requires": {
            "@babel/types": "^7.16.7"
          }
        }
      }
    },
    "@babel/plugin-transform-computed-properties": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-computed-properties/-/plugin-transform-computed-properties-7.16.7.tgz",
      "integrity": "sha512-gN72G9bcmenVILj//sv1zLNaPyYcOzUho2lIJBMh/iakJ9ygCo/hEF9cpGb61SCMEDxbbyBoVQxrt+bWKu5KGw==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-transform-destructuring": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-destructuring/-/plugin-transform-destructuring-7.16.7.tgz",
      "integrity": "sha512-VqAwhTHBnu5xBVDCvrvqJbtLUa++qZaWC0Fgr2mqokBlulZARGyIvZDoqbPlPaKImQ9dKAcCzbv+ul//uqu70A==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-transform-dotall-regex": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-dotall-regex/-/plugin-transform-dotall-regex-7.16.7.tgz",
      "integrity": "sha512-Lyttaao2SjZF6Pf4vk1dVKv8YypMpomAbygW+mU5cYP3S5cWTfCJjG8xV6CFdzGFlfWK81IjL9viiTvpb6G7gQ==",
      "dev": true,
      "requires": {
        "@babel/helper-create-regexp-features-plugin": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-transform-duplicate-keys": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-duplicate-keys/-/plugin-transform-duplicate-keys-7.16.7.tgz",
      "integrity": "sha512-03DvpbRfvWIXyK0/6QiR1KMTWeT6OcQ7tbhjrXyFS02kjuX/mu5Bvnh5SDSWHxyawit2g5aWhKwI86EE7GUnTw==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-transform-exponentiation-operator": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-exponentiation-operator/-/plugin-transform-exponentiation-operator-7.16.7.tgz",
      "integrity": "sha512-8UYLSlyLgRixQvlYH3J2ekXFHDFLQutdy7FfFAMm3CPZ6q9wHCwnUyiXpQCe3gVVnQlHc5nsuiEVziteRNTXEA==",
      "dev": true,
      "requires": {
        "@babel/helper-builder-binary-assignment-operator-visitor": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-transform-for-of": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-for-of/-/plugin-transform-for-of-7.16.7.tgz",
      "integrity": "sha512-/QZm9W92Ptpw7sjI9Nx1mbcsWz33+l8kuMIQnDwgQBG5s3fAfQvkRjQ7NqXhtNcKOnPkdICmUHyCaWW06HCsqg==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-transform-function-name": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-function-name/-/plugin-transform-function-name-7.16.7.tgz",
      "integrity": "sha512-SU/C68YVwTRxqWj5kgsbKINakGag0KTgq9f2iZEXdStoAbOzLHEBRYzImmA6yFo8YZhJVflvXmIHUO7GWHmxxA==",
      "dev": true,
      "requires": {
        "@babel/helper-compilation-targets": "^7.16.7",
        "@babel/helper-function-name": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-transform-literals": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-literals/-/plugin-transform-literals-7.16.7.tgz",
      "integrity": "sha512-6tH8RTpTWI0s2sV6uq3e/C9wPo4PTqqZps4uF0kzQ9/xPLFQtipynvmT1g/dOfEJ+0EQsHhkQ/zyRId8J2b8zQ==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-transform-member-expression-literals": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-member-expression-literals/-/plugin-transform-member-expression-literals-7.16.7.tgz",
      "integrity": "sha512-mBruRMbktKQwbxaJof32LT9KLy2f3gH+27a5XSuXo6h7R3vqltl0PgZ80C8ZMKw98Bf8bqt6BEVi3svOh2PzMw==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-transform-modules-amd": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-modules-amd/-/plugin-transform-modules-amd-7.16.7.tgz",
      "integrity": "sha512-KaaEtgBL7FKYwjJ/teH63oAmE3lP34N3kshz8mm4VMAw7U3PxjVwwUmxEFksbgsNUaO3wId9R2AVQYSEGRa2+g==",
      "dev": true,
      "requires": {
        "@babel/helper-module-transforms": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7",
        "babel-plugin-dynamic-import-node": "^2.3.3"
      }
    },
    "@babel/plugin-transform-modules-commonjs": {
      "version": "7.16.8",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-modules-commonjs/-/plugin-transform-modules-commonjs-7.16.8.tgz",
      "integrity": "sha512-oflKPvsLT2+uKQopesJt3ApiaIS2HW+hzHFcwRNtyDGieAeC/dIHZX8buJQ2J2X1rxGPy4eRcUijm3qcSPjYcA==",
      "dev": true,
      "requires": {
        "@babel/helper-module-transforms": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/helper-simple-access": "^7.16.7",
        "babel-plugin-dynamic-import-node": "^2.3.3"
      }
    },
    "@babel/plugin-transform-modules-systemjs": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-modules-systemjs/-/plugin-transform-modules-systemjs-7.16.7.tgz",
      "integrity": "sha512-DuK5E3k+QQmnOqBR9UkusByy5WZWGRxfzV529s9nPra1GE7olmxfqO2FHobEOYSPIjPBTr4p66YDcjQnt8cBmw==",
      "dev": true,
      "requires": {
        "@babel/helper-hoist-variables": "^7.16.7",
        "@babel/helper-module-transforms": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/helper-validator-identifier": "^7.16.7",
        "babel-plugin-dynamic-import-node": "^2.3.3"
      }
    },
    "@babel/plugin-transform-modules-umd": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-modules-umd/-/plugin-transform-modules-umd-7.16.7.tgz",
      "integrity": "sha512-EMh7uolsC8O4xhudF2F6wedbSHm1HHZ0C6aJ7K67zcDNidMzVcxWdGr+htW9n21klm+bOn+Rx4CBsAntZd3rEQ==",
      "dev": true,
      "requires": {
        "@babel/helper-module-transforms": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-transform-named-capturing-groups-regex": {
      "version": "7.16.8",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-named-capturing-groups-regex/-/plugin-transform-named-capturing-groups-regex-7.16.8.tgz",
      "integrity": "sha512-j3Jw+n5PvpmhRR+mrgIh04puSANCk/T/UA3m3P1MjJkhlK906+ApHhDIqBQDdOgL/r1UYpz4GNclTXxyZrYGSw==",
      "dev": true,
      "requires": {
        "@babel/helper-create-regexp-features-plugin": "^7.16.7"
      }
    },
    "@babel/plugin-transform-new-target": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-new-target/-/plugin-transform-new-target-7.16.7.tgz",
      "integrity": "sha512-xiLDzWNMfKoGOpc6t3U+etCE2yRnn3SM09BXqWPIZOBpL2gvVrBWUKnsJx0K/ADi5F5YC5f8APFfWrz25TdlGg==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-transform-object-super": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-object-super/-/plugin-transform-object-super-7.16.7.tgz",
      "integrity": "sha512-14J1feiQVWaGvRxj2WjyMuXS2jsBkgB3MdSN5HuC2G5nRspa5RK9COcs82Pwy5BuGcjb+fYaUj94mYcOj7rCvw==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/helper-replace-supers": "^7.16.7"
      }
    },
    "@babel/plugin-transform-parameters": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-parameters/-/plugin-transform-parameters-7.16.7.tgz",
      "integrity": "sha512-AT3MufQ7zZEhU2hwOA11axBnExW0Lszu4RL/tAlUJBuNoRak+wehQW8h6KcXOcgjY42fHtDxswuMhMjFEuv/aw==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-transform-property-literals": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-property-literals/-/plugin-transform-property-literals-7.16.7.tgz",
      "integrity": "sha512-z4FGr9NMGdoIl1RqavCqGG+ZuYjfZ/hkCIeuH6Do7tXmSm0ls11nYVSJqFEUOSJbDab5wC6lRE/w6YjVcr6Hqw==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-transform-regenerator": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-regenerator/-/plugin-transform-regenerator-7.16.7.tgz",
      "integrity": "sha512-mF7jOgGYCkSJagJ6XCujSQg+6xC1M77/03K2oBmVJWoFGNUtnVJO4WHKJk3dnPC8HCcj4xBQP1Egm8DWh3Pb3Q==",
      "dev": true,
      "requires": {
        "regenerator-transform": "^0.14.2"
      }
    },
    "@babel/plugin-transform-reserved-words": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-reserved-words/-/plugin-transform-reserved-words-7.16.7.tgz",
      "integrity": "sha512-KQzzDnZ9hWQBjwi5lpY5v9shmm6IVG0U9pB18zvMu2i4H90xpT4gmqwPYsn8rObiadYe2M0gmgsiOIF5A/2rtg==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-transform-runtime": {
      "version": "7.16.4",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-runtime/-/plugin-transform-runtime-7.16.4.tgz",
      "integrity": "sha512-pru6+yHANMTukMtEZGC4fs7XPwg35v8sj5CIEmE+gEkFljFiVJxEWxx/7ZDkTK+iZRYo1bFXBtfIN95+K3cJ5A==",
      "dev": true,
      "requires": {
        "@babel/helper-module-imports": "^7.16.0",
        "@babel/helper-plugin-utils": "^7.14.5",
        "babel-plugin-polyfill-corejs2": "^0.3.0",
        "babel-plugin-polyfill-corejs3": "^0.4.0",
        "babel-plugin-polyfill-regenerator": "^0.3.0",
        "semver": "^6.3.0"
      },
      "dependencies": {
        "semver": {
          "version": "6.3.0",
          "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.0.tgz",
          "integrity": "sha512-b39TBaTSfV6yBrapU89p5fKekE2m/NwnDocOVruQFS1/veMgdzuPcnOM34M6CwxW8jH/lxEa5rBoDeUwu5HHTw==",
          "dev": true
        }
      }
    },
    "@babel/plugin-transform-shorthand-properties": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-shorthand-properties/-/plugin-transform-shorthand-properties-7.16.7.tgz",
      "integrity": "sha512-hah2+FEnoRoATdIb05IOXf+4GzXYTq75TVhIn1PewihbpyrNWUt2JbudKQOETWw6QpLe+AIUpJ5MVLYTQbeeUg==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-transform-spread": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-spread/-/plugin-transform-spread-7.16.7.tgz",
      "integrity": "sha512-+pjJpgAngb53L0iaA5gU/1MLXJIfXcYepLgXB3esVRf4fqmj8f2cxM3/FKaHsZms08hFQJkFccEWuIpm429TXg==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7",
        "@babel/helper-skip-transparent-expression-wrappers": "^7.16.0"
      }
    },
    "@babel/plugin-transform-sticky-regex": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-sticky-regex/-/plugin-transform-sticky-regex-7.16.7.tgz",
      "integrity": "sha512-NJa0Bd/87QV5NZZzTuZG5BPJjLYadeSZ9fO6oOUoL4iQx+9EEuw/eEM92SrsT19Yc2jgB1u1hsjqDtH02c3Drw==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-transform-template-literals": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-template-literals/-/plugin-transform-template-literals-7.16.7.tgz",
      "integrity": "sha512-VwbkDDUeenlIjmfNeDX/V0aWrQH2QiVyJtwymVQSzItFDTpxfyJh3EVaQiS0rIN/CqbLGr0VcGmuwyTdZtdIsA==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-transform-typeof-symbol": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-typeof-symbol/-/plugin-transform-typeof-symbol-7.16.7.tgz",
      "integrity": "sha512-p2rOixCKRJzpg9JB4gjnG4gjWkWa89ZoYUnl9snJ1cWIcTH/hvxZqfO+WjG6T8DRBpctEol5jw1O5rA8gkCokQ==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-transform-unicode-escapes": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-unicode-escapes/-/plugin-transform-unicode-escapes-7.16.7.tgz",
      "integrity": "sha512-TAV5IGahIz3yZ9/Hfv35TV2xEm+kaBDaZQCn2S/hG9/CZ0DktxJv9eKfPc7yYCvOYR4JGx1h8C+jcSOvgaaI/Q==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/plugin-transform-unicode-regex": {
      "version": "7.16.7",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-unicode-regex/-/plugin-transform-unicode-regex-7.16.7.tgz",
      "integrity": "sha512-oC5tYYKw56HO75KZVLQ+R/Nl3Hro9kf8iG0hXoaHP7tjAyCpvqBiSNe6vGrZni1Z6MggmUOC6A7VP7AVmw225Q==",
      "dev": true,
      "requires": {
        "@babel/helper-create-regexp-features-plugin": "^7.16.7",
        "@babel/helper-plugin-utils": "^7.16.7"
      }
    },
    "@babel/preset-env": {
      "version": "7.16.4",
      "resolved": "https://registry.npmjs.org/@babel/preset-env/-/preset-env-7.16.4.tgz",
      "integrity": "sha512-v0QtNd81v/xKj4gNKeuAerQ/azeNn/G1B1qMLeXOcV8+4TWlD2j3NV1u8q29SDFBXx/NBq5kyEAO+0mpRgacjA==",
      "dev": true,
      "requires": {
        "@babel/compat-data": "^7.16.4",
        "@babel/helper-compilation-targets": "^7.16.3",
        "@babel/helper-plugin-utils": "^7.14.5",
        "@babel/helper-validator-option": "^7.14.5",
        "@babel/plugin-bugfix-safari-id-destructuring-collision-in-function-expression": "^7.16.2",
        "@babel/plugin-bugfix-v8-spread-parameters-in-optional-chaining": "^7.16.0",
        "@babel/plugin-proposal-async-generator-functions": "^7.16.4",
        "@babel/plugin-proposal-class-properties": "^7.16.0",
        "@babel/plugin-proposal-class-static-block": "^7.16.0",
        "@babel/plugin-proposal-dynamic-import": "^7.16.0",
        "@babel/plugin-proposal-export-namespace-from": "^7.16.0",
        "@babel/plugin-proposal-json-strings": "^7.16.0",
        "@babel/plugin-proposal-logical-assignment-operators": "^7.16.0",
        "@babel/plugin-proposal-nullish-coalescing-operator": "^7.16.0",
        "@babel/plugin-proposal-numeric-separator": "^7.16.0",
        "@babel/plugin-proposal-object-rest-spread": "^7.16.0",
        "@babel/plugin-proposal-optional-catch-binding": "^7.16.0",
        "@babel/plugin-proposal-optional-chaining": "^7.16.0",
        "@babel/plugin-proposal-private-methods": "^7.16.0",
        "@babel/plugin-proposal-private-property-in-object": "^7.16.0",
        "@babel/plugin-proposal-unicode-property-regex": "^7.16.0",
        "@babel/plugin-syntax-async-generators": "^7.8.4",
        "@babel/plugin-syntax-class-properties": "^7.12.13",
        "@babel/plugin-syntax-class-static-block": "^7.14.5",
        "@babel/plugin-syntax-dynamic-import": "^7.8.3",
        "@babel/plugin-syntax-export-namespace-from": "^7.8.3",
        "@babel/plugin-syntax-json-strings": "^7.8.3",
        "@babel/plugin-syntax-logical-assignment-operators": "^7.10.4",
        "@babel/plugin-syntax-nullish-coalescing-operator": "^7.8.3",
        "@babel/plugin-syntax-numeric-separator": "^7.10.4",
        "@babel/plugin-syntax-object-rest-spread": "^7.8.3",
        "@babel/plugin-syntax-optional-catch-binding": "^7.8.3",
        "@babel/plugin-syntax-optional-chaining": "^7.8.3",
        "@babel/plugin-syntax-private-property-in-object": "^7.14.5",
        "@babel/plugin-syntax-top-level-await": "^7.14.5",
        "@babel/plugin-transform-arrow-functions": "^7.16.0",
        "@babel/plugin-transform-async-to-generator": "^7.16.0",
        "@babel/plugin-transform-block-scoped-functions": "^7.16.0",
        "@babel/plugin-transform-block-scoping": "^7.16.0",
        "@babel/plugin-transform-classes": "^7.16.0",
        "@babel/plugin-transform-computed-properties": "^7.16.0",
        "@babel/plugin-transform-destructuring": "^7.16.0",
        "@babel/plugin-transform-dotall-regex": "^7.16.0",
        "@babel/plugin-transform-duplicate-keys": "^7.16.0",
        "@babel/plugin-transform-exponentiation-operator": "^7.16.0",
        "@babel/plugin-transform-for-of": "^7.16.0",
        "@babel/plugin-transform-function-name": "^7.16.0",
        "@babel/plugin-transform-literals": "^7.16.0",
        "@babel/plugin-transform-member-expression-literals": "^7.16.0",
        "@babel/plugin-transform-modules-amd": "^7.16.0",
        "@babel/plugin-transform-modules-commonjs": "^7.16.0",
        "@babel/plugin-transform-modules-systemjs": "^7.16.0",
        "@babel/plugin-transform-modules-umd": "^7.16.0",
        "@babel/plugin-transform-named-capturing-groups-regex": "^7.16.0",
        "@babel/plugin-transform-new-target": "^7.16.0",
        "@babel/plugin-transform-object-super": "^7.16.0",
        "@babel/plugin-transform-parameters": "^7.16.3",
        "@babel/plugin-transform-property-literals": "^7.16.0",
        "@babel/plugin-transform-regenerator": "^7.16.0",
        "@babel/plugin-transform-reserved-words": "^7.16.0",
        "@babel/plugin-transform-shorthand-properties": "^7.16.0",
        "@babel/plugin-transform-spread": "^7.16.0",
        "@babel/plugin-transform-sticky-regex": "^7.16.0",
        "@babel/plugin-transform-template-literals": "^7.16.0",
        "@babel/plugin-transform-typeof-symbol": "^7.16.0",
        "@babel/plugin-transform-unicode-escapes": "^7.16.0",
        "@babel/plugin-transform-unicode-regex": "^7.16.0",
        "@babel/preset-modules": "^0.1.5",
        "@babel/types": "^7.16.0",
        "babel-plugin-polyfill-corejs2": "^0.3.0",
        "babel-plugin-polyfill-corejs3": "^0.4.0",
        "babel-plugin-polyfill-regenerator": "^0.3.0",
        "core-js-compat": "^3.19.1",
        "semver": "^6.3.0"
      },
      "dependencies": {
        "semver": {
          "version": "6.3.0",
          "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.0.tgz",
          "integrity": "sha512-b39TBaTSfV6yBrapU89p5fKekE2m/NwnDocOVruQFS1/veMgdzuPcnOM34M6CwxW8jH/lxEa5rBoDeUwu5HHTw==",
          "dev": true
        }
      }
    },
    "@babel/preset-modules": {
      "version": "0.1.5",
      "resolved": "https://registry.npmjs.org/@babel/preset-modules/-/preset-modules-0.1.5.tgz",
      "integrity": "sha512-A57th6YRG7oR3cq/yt/Y84MvGgE0eJG2F1JLhKuyG+jFxEgrd/HAMJatiFtmOiZurz+0DkrvbheCLaV5f2JfjA==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.0.0",
        "@babel/plugin-proposal-unicode-property-regex": "^7.4.4",
        "@babel/plugin-transform-dotall-regex": "^7.4.4",
        "@babel/types": "^7.4.4",
        "esutils": "^2.0.2"
      }
    },
    "@babel/runtime": {
      "version": "7.16.3",
      "resolved": "https://registry.npmjs.org/@babel/runtime/-/runtime-7.16.3.tgz",
      "integrity": "sha512-WBwekcqacdY2e9AF/Q7WLFUWmdJGJTkbjqTjoMDgXkVZ3ZRUvOPsLb5KdwISoQVsbP+DQzVZW4Zhci0DvpbNTQ==",
      "dev": true,
      "requires": {
        "regenerator-runtime": "^0.13.4"
      }
    },
    "@babel/template": {
      "version": "7.16.0",
      "resolved": "https://registry.npmjs.org/@babel/template/-/template-7.16.0.tgz",
      "integrity": "sha512-MnZdpFD/ZdYhXwiunMqqgyZyucaYsbL0IrjoGjaVhGilz+x8YB++kRfygSOIj1yOtWKPlx7NBp+9I1RQSgsd5A==",
      "dev": true,
      "requires": {
        "@babel/code-frame": "^7.16.0",
        "@babel/parser": "^7.16.0",
        "@babel/types": "^7.16.0"
      }
    },
    "@babel/traverse": {
      "version": "7.16.10",
      "resolved": "https://registry.npmjs.org/@babel/traverse/-/traverse-7.16.10.tgz",
      "integrity": "sha512-yzuaYXoRJBGMlBhsMJoUW7G1UmSb/eXr/JHYM/MsOJgavJibLwASijW7oXBdw3NQ6T0bW7Ty5P/VarOs9cHmqw==",
      "dev": true,
      "requires": {
        "@babel/code-frame": "^7.16.7",
        "@babel/generator": "^7.16.8",
        "@babel/helper-environment-visitor": "^7.16.7",
        "@babel/helper-function-name": "^7.16.7",
        "@babel/helper-hoist-variables": "^7.16.7",
        "@babel/helper-split-export-declaration": "^7.16.7",
        "@babel/parser": "^7.16.10",
        "@babel/types": "^7.16.8",
        "debug": "^4.1.0",
        "globals": "^11.1.0"
      },
      "dependencies": {
        "@babel/generator": {
          "version": "7.16.8",
          "resolved": "https://registry.npmjs.org/@babel/generator/-/generator-7.16.8.tgz",
          "integrity": "sha512-1ojZwE9+lOXzcWdWmO6TbUzDfqLD39CmEhN8+2cX9XkDo5yW1OpgfejfliysR2AWLpMamTiOiAp/mtroaymhpw==",
          "dev": true,
          "requires": {
            "@babel/types": "^7.16.8",
            "jsesc": "^2.5.1",
            "source-map": "^0.5.0"
          }
        },
        "source-map": {
          "version": "0.5.7",
          "resolved": "https://registry.npmjs.org/source-map/-/source-map-0.5.7.tgz",
          "integrity": "sha1-igOdLRAh0i0eoUyA2OpGi6LvP8w=",
          "dev": true
        }
      }
    },
    "@babel/types": {
      "version": "7.16.8",
      "resolved": "https://registry.npmjs.org/@babel/types/-/types-7.16.8.tgz",
      "integrity": "sha512-smN2DQc5s4M7fntyjGtyIPbRJv6wW4rU/94fmYJ7PKQuZkC0qGMHXJbg6sNGt12JmVr4k5YaptI/XtiLJBnmIg==",
      "dev": true,
      "requires": {
        "@babel/helper-validator-identifier": "^7.16.7",
        "to-fast-properties": "^2.0.0"
      }
    },
    "@discoveryjs/json-ext": {
      "version": "0.5.6",
      "resolved": "https://registry.npmjs.org/@discoveryjs/json-ext/-/json-ext-0.5.6.tgz",
      "integrity": "sha512-ws57AidsDvREKrZKYffXddNkyaF14iHNHm8VQnZH6t99E8gczjNN0GpvcGny0imC80yQ0tHz1xVUKk/KFQSUyA==",
      "dev": true
    },
    "@gar/promisify": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/@gar/promisify/-/promisify-1.1.2.tgz",
      "integrity": "sha512-82cpyJyKRoQoRi+14ibCeGPu0CwypgtBAdBhq1WfvagpCZNKqwXbKwXllYSMG91DhmG4jt9gN8eP6lGOtozuaw==",
      "dev": true
    },
    "@istanbuljs/load-nyc-config": {
      "version": "1.1.0",
      "resolved": "https://registry.npmjs.org/@istanbuljs/load-nyc-config/-/load-nyc-config-1.1.0.tgz",
      "integrity": "sha512-VjeHSlIzpv/NyD3N0YuHfXOPDIixcA1q2ZV98wsMqcYlPmv2n3Yb2lYP9XMElnaFVXg5A7YLTeLu6V84uQDjmQ==",
      "dev": true,
      "requires": {
        "camelcase": "^5.3.1",
        "find-up": "^4.1.0",
        "get-package-type": "^0.1.0",
        "js-yaml": "^3.13.1",
        "resolve-from": "^5.0.0"
      }
    },
    "@istanbuljs/schema": {
      "version": "0.1.3",
      "resolved": "https://registry.npmjs.org/@istanbuljs/schema/-/schema-0.1.3.tgz",
      "integrity": "sha512-ZXRY4jNvVgSVQ8DL3LTcakaAtXwTVUxE81hslsyD2AtoXW/wVob10HkOJ1X/pAlcI7D+2YoZKg5do8G/w6RYgA==",
      "dev": true
    },
    "@jridgewell/resolve-uri": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/@jridgewell/resolve-uri/-/resolve-uri-1.0.0.tgz",
      "integrity": "sha512-9oLAnygRMi8Q5QkYEU4XWK04B+nuoXoxjRvRxgjuChkLZFBja0YPSgdZ7dZtwhncLBcQe/I/E+fLuk5qxcYVJA==",
      "dev": true
    },
    "@ngtools/webpack": {
      "version": "13.1.4",
      "resolved": "https://registry.npmjs.org/@ngtools/webpack/-/webpack-13.1.4.tgz",
      "integrity": "sha512-s8gzjG2nYHawFhlkHMkQWYrocHkBI1nF6T9K/oCSTIsq6kvTv//Ahno2VdBSgVq8uMnpv1TymvX0nFC4Dgn1HA==",
      "dev": true,
      "requires": {}
    },
    "@nodelib/fs.scandir": {
      "version": "2.1.5",
      "resolved": "https://registry.npmjs.org/@nodelib/fs.scandir/-/fs.scandir-2.1.5.tgz",
      "integrity": "sha512-vq24Bq3ym5HEQm2NKCr3yXDwjc7vTsEThRDnkp2DK9p1uqLR+DHurm/NOTo0KG7HYHU7eppKZj3MyqYuMBf62g==",
      "dev": true,
      "requires": {
        "@nodelib/fs.stat": "2.0.5",
        "run-parallel": "^1.1.9"
      }
    },
    "@nodelib/fs.stat": {
      "version": "2.0.5",
      "resolved": "https://registry.npmjs.org/@nodelib/fs.stat/-/fs.stat-2.0.5.tgz",
      "integrity": "sha512-RkhPPp2zrqDAQA/2jNhnztcPAlv64XdhIp7a7454A5ovI7Bukxgt7MX7udwAu3zg1DcpPU0rz3VV1SeaqvY4+A==",
      "dev": true
    },
    "@nodelib/fs.walk": {
      "version": "1.2.8",
      "resolved": "https://registry.npmjs.org/@nodelib/fs.walk/-/fs.walk-1.2.8.tgz",
      "integrity": "sha512-oGB+UxlgWcgQkgwo8GcEGwemoTFt3FIO9ababBmaGwXIoBKZ+GTy0pP185beGg7Llih/NSHSV2XAs1lnznocSg==",
      "dev": true,
      "requires": {
        "@nodelib/fs.scandir": "2.1.5",
        "fastq": "^1.6.0"
      }
    },
    "@npmcli/fs": {
      "version": "1.1.0",
      "resolved": "https://registry.npmjs.org/@npmcli/fs/-/fs-1.1.0.tgz",
      "integrity": "sha512-VhP1qZLXcrXRIaPoqb4YA55JQxLNF3jNR4T55IdOJa3+IFJKNYHtPvtXx8slmeMavj37vCzCfrqQM1vWLsYKLA==",
      "dev": true,
      "requires": {
        "@gar/promisify": "^1.0.1",
        "semver": "^7.3.5"
      }
    },
    "@npmcli/git": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/@npmcli/git/-/git-2.1.0.tgz",
      "integrity": "sha512-/hBFX/QG1b+N7PZBFs0bi+evgRZcK9nWBxQKZkGoXUT5hJSwl5c4d7y8/hm+NQZRPhQ67RzFaj5UM9YeyKoryw==",
      "dev": true,
      "requires": {
        "@npmcli/promise-spawn": "^1.3.2",
        "lru-cache": "^6.0.0",
        "mkdirp": "^1.0.4",
        "npm-pick-manifest": "^6.1.1",
        "promise-inflight": "^1.0.1",
        "promise-retry": "^2.0.1",
        "semver": "^7.3.5",
        "which": "^2.0.2"
      },
      "dependencies": {
        "which": {
          "version": "2.0.2",
          "resolved": "https://registry.npmjs.org/which/-/which-2.0.2.tgz",
          "integrity": "sha512-BLI3Tl1TW3Pvl70l3yq3Y64i+awpwXqsGBYWkkqMtnbXgrMD+yj7rhW0kuEDxzJaYXGjEW5ogapKNMEKNMjibA==",
          "dev": true,
          "requires": {
            "isexe": "^2.0.0"
          }
        }
      }
    },
    "@npmcli/installed-package-contents": {
      "version": "1.0.7",
      "resolved": "https://registry.npmjs.org/@npmcli/installed-package-contents/-/installed-package-contents-1.0.7.tgz",
      "integrity": "sha512-9rufe0wnJusCQoLpV9ZPKIVP55itrM5BxOXs10DmdbRfgWtHy1LDyskbwRnBghuB0PrF7pNPOqREVtpz4HqzKw==",
      "dev": true,
      "requires": {
        "npm-bundled": "^1.1.1",
        "npm-normalize-package-bin": "^1.0.1"
      }
    },
    "@npmcli/move-file": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/@npmcli/move-file/-/move-file-1.1.2.tgz",
      "integrity": "sha512-1SUf/Cg2GzGDyaf15aR9St9TWlb+XvbZXWpDx8YKs7MLzMH/BCeopv+y9vzrzgkfykCGuWOlSu3mZhj2+FQcrg==",
      "dev": true,
      "requires": {
        "mkdirp": "^1.0.4",
        "rimraf": "^3.0.2"
      }
    },
    "@npmcli/node-gyp": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/@npmcli/node-gyp/-/node-gyp-1.0.3.tgz",
      "integrity": "sha512-fnkhw+fmX65kiLqk6E3BFLXNC26rUhK90zVwe2yncPliVT/Qos3xjhTLE59Df8KnPlcwIERXKVlU1bXoUQ+liA==",
      "dev": true
    },
    "@npmcli/promise-spawn": {
      "version": "1.3.2",
      "resolved": "https://registry.npmjs.org/@npmcli/promise-spawn/-/promise-spawn-1.3.2.tgz",
      "integrity": "sha512-QyAGYo/Fbj4MXeGdJcFzZ+FkDkomfRBrPM+9QYJSg+PxgAUL+LU3FneQk37rKR2/zjqkCV1BLHccX98wRXG3Sg==",
      "dev": true,
      "requires": {
        "infer-owner": "^1.0.4"
      }
    },
    "@npmcli/run-script": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/@npmcli/run-script/-/run-script-2.0.0.tgz",
      "integrity": "sha512-fSan/Pu11xS/TdaTpTB0MRn9guwGU8dye+x56mEVgBEd/QsybBbYcAL0phPXi8SGWFEChkQd6M9qL4y6VOpFig==",
      "dev": true,
      "requires": {
        "@npmcli/node-gyp": "^1.0.2",
        "@npmcli/promise-spawn": "^1.3.2",
        "node-gyp": "^8.2.0",
        "read-package-json-fast": "^2.0.1"
      }
    },
    "@popperjs/core": {
      "version": "2.11.2",
      "resolved": "https://registry.npmjs.org/@popperjs/core/-/core-2.11.2.tgz",
      "integrity": "sha512-92FRmppjjqz29VMJ2dn+xdyXZBrMlE42AV6Kq6BwjWV7CNUW1hs2FtxSNLQE+gJhaZ6AAmYuO9y8dshhcBl7vA==",
      "peer": true
    },
    "@schematics/angular": {
      "version": "13.1.4",
      "resolved": "https://registry.npmjs.org/@schematics/angular/-/angular-13.1.4.tgz",
      "integrity": "sha512-P1YsHn1LLAmdpB9X2TBuUgrvEW/KaoBbHr8ifYO8/uQEXyeiIF+So8h/dnegkYkdsr3OwQ2X/j3UF6/+HS0odg==",
      "dev": true,
      "requires": {
        "@angular-devkit/core": "13.1.4",
        "@angular-devkit/schematics": "13.1.4",
        "jsonc-parser": "3.0.0"
      }
    },
    "@sindresorhus/is": {
      "version": "0.14.0",
      "resolved": "https://registry.npmjs.org/@sindresorhus/is/-/is-0.14.0.tgz",
      "integrity": "sha512-9NET910DNaIPngYnLLPeg+Ogzqsi9uM4mSboU5y6p8S5DzMTVEsJZrawi+BoDNUVBa2DhJqQYUFvMDfgU062LQ=="
    },
    "@socket.io/base64-arraybuffer": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/@socket.io/base64-arraybuffer/-/base64-arraybuffer-1.0.2.tgz",
      "integrity": "sha512-dOlCBKnDw4iShaIsH/bxujKTM18+2TOAsYz+KSc11Am38H4q5Xw8Bbz97ZYdrVNM+um3p7w86Bvvmcn9q+5+eQ==",
      "dev": true
    },
    "@szmarczak/http-timer": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/@szmarczak/http-timer/-/http-timer-1.1.2.tgz",
      "integrity": "sha512-XIB2XbzHTN6ieIjfIMV9hlVcfPU26s2vafYWQcZHWXHOxiaRZYEDKEwdl129Zyg50+foYV2jCgtrqSA6qNuNSA==",
      "requires": {
        "defer-to-connect": "^1.0.1"
      }
    },
    "@tootallnate/once": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/@tootallnate/once/-/once-1.1.2.tgz",
      "integrity": "sha512-RbzJvlNzmRq5c3O09UipeuXno4tA1FE6ikOjxZK0tuxVv3412l64l5t1W5pj4+rJq9vpkm/kwiR07aZXnsKPxw==",
      "dev": true
    },
    "@types/body-parser": {
      "version": "1.19.2",
      "resolved": "https://registry.npmjs.org/@types/body-parser/-/body-parser-1.19.2.tgz",
      "integrity": "sha512-ALYone6pm6QmwZoAgeyNksccT9Q4AWZQ6PvfwR37GT6r6FWUPguq6sUmNGSMV2Wr761oQoBxwGGa6DR5o1DC9g==",
      "dev": true,
      "peer": true,
      "requires": {
        "@types/connect": "*",
        "@types/node": "*"
      }
    },
    "@types/component-emitter": {
      "version": "1.2.11",
      "resolved": "https://registry.npmjs.org/@types/component-emitter/-/component-emitter-1.2.11.tgz",
      "integrity": "sha512-SRXjM+tfsSlA9VuG8hGO2nft2p8zjXCK1VcC6N4NXbBbYbSia9kzCChYQajIjzIqOOOuh5Ock6MmV2oux4jDZQ==",
      "dev": true
    },
    "@types/connect": {
      "version": "3.4.35",
      "resolved": "https://registry.npmjs.org/@types/connect/-/connect-3.4.35.tgz",
      "integrity": "sha512-cdeYyv4KWoEgpBISTxWvqYsVy444DOqehiF3fM3ne10AmJ62RSyNkUnxMJXHQWRQQX2eR94m5y1IZyDwBjV9FQ==",
      "dev": true,
      "peer": true,
      "requires": {
        "@types/node": "*"
      }
    },
    "@types/cookie": {
      "version": "0.4.1",
      "resolved": "https://registry.npmjs.org/@types/cookie/-/cookie-0.4.1.tgz",
      "integrity": "sha512-XW/Aa8APYr6jSVVA1y/DEIZX0/GMKLEVekNG727R8cs56ahETkRAy/3DR7+fJyh7oUgGwNQaRfXCun0+KbWY7Q==",
      "dev": true
    },
    "@types/cors": {
      "version": "2.8.12",
      "resolved": "https://registry.npmjs.org/@types/cors/-/cors-2.8.12.tgz",
      "integrity": "sha512-vt+kDhq/M2ayberEtJcIN/hxXy1Pk+59g2FV/ZQceeaTyCtCucjL2Q7FXlFjtWn4n15KCr1NE2lNNFhp0lEThw==",
      "dev": true
    },
    "@types/eslint": {
      "version": "8.4.1",
      "resolved": "https://registry.npmjs.org/@types/eslint/-/eslint-8.4.1.tgz",
      "integrity": "sha512-GE44+DNEyxxh2Kc6ro/VkIj+9ma0pO0bwv9+uHSyBrikYOHr8zYcdPvnBOp1aw8s+CjRvuSx7CyWqRrNFQ59mA==",
      "dev": true,
      "requires": {
        "@types/estree": "*",
        "@types/json-schema": "*"
      }
    },
    "@types/eslint-scope": {
      "version": "3.7.3",
      "resolved": "https://registry.npmjs.org/@types/eslint-scope/-/eslint-scope-3.7.3.tgz",
      "integrity": "sha512-PB3ldyrcnAicT35TWPs5IcwKD8S333HMaa2VVv4+wdvebJkjWuW/xESoB8IwRcog8HYVYamb1g/R31Qv5Bx03g==",
      "dev": true,
      "requires": {
        "@types/eslint": "*",
        "@types/estree": "*"
      }
    },
    "@types/estree": {
      "version": "0.0.50",
      "resolved": "https://registry.npmjs.org/@types/estree/-/estree-0.0.50.tgz",
      "integrity": "sha512-C6N5s2ZFtuZRj54k2/zyRhNDjJwwcViAM3Nbm8zjBpbqAdZ00mr0CFxvSKeO8Y/e03WVFLpQMdHYVfUd6SB+Hw==",
      "dev": true
    },
    "@types/express": {
      "version": "4.17.13",
      "resolved": "https://registry.npmjs.org/@types/express/-/express-4.17.13.tgz",
      "integrity": "sha512-6bSZTPaTIACxn48l50SR+axgrqm6qXFIxrdAKaG6PaJk3+zuUr35hBlgT7vOmJcum+OEaIBLtHV/qloEAFITeA==",
      "dev": true,
      "peer": true,
      "requires": {
        "@types/body-parser": "*",
        "@types/express-serve-static-core": "^4.17.18",
        "@types/qs": "*",
        "@types/serve-static": "*"
      }
    },
    "@types/express-serve-static-core": {
      "version": "4.17.28",
      "resolved": "https://registry.npmjs.org/@types/express-serve-static-core/-/express-serve-static-core-4.17.28.tgz",
      "integrity": "sha512-P1BJAEAW3E2DJUlkgq4tOL3RyMunoWXqbSCygWo5ZIWTjUgN1YnaXWW4VWl/oc8vs/XoYibEGBKP0uZyF4AHig==",
      "dev": true,
      "peer": true,
      "requires": {
        "@types/node": "*",
        "@types/qs": "*",
        "@types/range-parser": "*"
      }
    },
    "@types/http-proxy": {
      "version": "1.17.8",
      "resolved": "https://registry.npmjs.org/@types/http-proxy/-/http-proxy-1.17.8.tgz",
      "integrity": "sha512-5kPLG5BKpWYkw/LVOGWpiq3nEVqxiN32rTgI53Sk12/xHFQ2rG3ehI9IO+O3W2QoKeyB92dJkoka8SUm6BX1pA==",
      "dev": true,
      "requires": {
        "@types/node": "*"
      }
    },
    "@types/jasmine": {
      "version": "3.10.3",
      "resolved": "https://registry.npmjs.org/@types/jasmine/-/jasmine-3.10.3.tgz",
      "integrity": "sha512-SWyMrjgdAUHNQmutvDcKablrJhkDLy4wunTme8oYLjKp41GnHGxMRXr2MQMvy/qy8H3LdzwQk9gH4hZ6T++H8g==",
      "dev": true
    },
    "@types/json-schema": {
      "version": "7.0.9",
      "resolved": "https://registry.npmjs.org/@types/json-schema/-/json-schema-7.0.9.tgz",
      "integrity": "sha512-qcUXuemtEu+E5wZSJHNxUXeCZhAfXKQ41D+duX+VYPde7xyEVZci+/oXKJL13tnRs9lR2pr4fod59GT6/X1/yQ==",
      "dev": true
    },
    "@types/mime": {
      "version": "1.3.2",
      "resolved": "https://registry.npmjs.org/@types/mime/-/mime-1.3.2.tgz",
      "integrity": "sha512-YATxVxgRqNH6nHEIsvg6k2Boc1JHI9ZbH5iWFFv/MTkchz3b1ieGDa5T0a9RznNdI0KhVbdbWSN+KWWrQZRxTw==",
      "dev": true,
      "peer": true
    },
    "@types/node": {
      "version": "12.20.42",
      "resolved": "https://registry.npmjs.org/@types/node/-/node-12.20.42.tgz",
      "integrity": "sha512-aI3/oo5DzyiI5R/xAhxxRzfZlWlsbbqdgxfTPkqu/Zt+23GXiJvMCyPJT4+xKSXOnLqoL8jJYMLTwvK2M3a5hw==",
      "dev": true
    },
    "@types/parse-json": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/@types/parse-json/-/parse-json-4.0.0.tgz",
      "integrity": "sha512-//oorEZjL6sbPcKUaCdIGlIUeH26mgzimjBB77G6XRgnDl/L5wOnpyBGRe/Mmf5CVW3PwEBE1NjiMZ/ssFh4wA==",
      "dev": true
    },
    "@types/qs": {
      "version": "6.9.7",
      "resolved": "https://registry.npmjs.org/@types/qs/-/qs-6.9.7.tgz",
      "integrity": "sha512-FGa1F62FT09qcrueBA6qYTrJPVDzah9a+493+o2PCXsesWHIn27G98TsSMs3WPNbZIEj4+VJf6saSFpvD+3Zsw==",
      "dev": true,
      "peer": true
    },
    "@types/range-parser": {
      "version": "1.2.4",
      "resolved": "https://registry.npmjs.org/@types/range-parser/-/range-parser-1.2.4.tgz",
      "integrity": "sha512-EEhsLsD6UsDM1yFhAvy0Cjr6VwmpMWqFBCb9w07wVugF7w9nfajxLuVmngTIpgS6svCnm6Vaw+MZhoDCKnOfsw==",
      "dev": true,
      "peer": true
    },
    "@types/retry": {
      "version": "0.12.1",
      "resolved": "https://registry.npmjs.org/@types/retry/-/retry-0.12.1.tgz",
      "integrity": "sha512-xoDlM2S4ortawSWORYqsdU+2rxdh4LRW9ytc3zmT37RIKQh6IHyKwwtKhKis9ah8ol07DCkZxPt8BBvPjC6v4g==",
      "dev": true
    },
    "@types/serve-static": {
      "version": "1.13.10",
      "resolved": "https://registry.npmjs.org/@types/serve-static/-/serve-static-1.13.10.tgz",
      "integrity": "sha512-nCkHGI4w7ZgAdNkrEu0bv+4xNV/XDqW+DydknebMOQwkpDGx8G+HTlj7R7ABI8i8nKxVw0wtKPi1D+lPOkh4YQ==",
      "dev": true,
      "peer": true,
      "requires": {
        "@types/mime": "^1",
        "@types/node": "*"
      }
    },
    "@webassemblyjs/ast": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/ast/-/ast-1.11.1.tgz",
      "integrity": "sha512-ukBh14qFLjxTQNTXocdyksN5QdM28S1CxHt2rdskFyL+xFV7VremuBLVbmCePj+URalXBENx/9Lm7lnhihtCSw==",
      "dev": true,
      "requires": {
        "@webassemblyjs/helper-numbers": "1.11.1",
        "@webassemblyjs/helper-wasm-bytecode": "1.11.1"
      }
    },
    "@webassemblyjs/floating-point-hex-parser": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/floating-point-hex-parser/-/floating-point-hex-parser-1.11.1.tgz",
      "integrity": "sha512-iGRfyc5Bq+NnNuX8b5hwBrRjzf0ocrJPI6GWFodBFzmFnyvrQ83SHKhmilCU/8Jv67i4GJZBMhEzltxzcNagtQ==",
      "dev": true
    },
    "@webassemblyjs/helper-api-error": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/helper-api-error/-/helper-api-error-1.11.1.tgz",
      "integrity": "sha512-RlhS8CBCXfRUR/cwo2ho9bkheSXG0+NwooXcc3PAILALf2QLdFyj7KGsKRbVc95hZnhnERon4kW/D3SZpp6Tcg==",
      "dev": true
    },
    "@webassemblyjs/helper-buffer": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/helper-buffer/-/helper-buffer-1.11.1.tgz",
      "integrity": "sha512-gwikF65aDNeeXa8JxXa2BAk+REjSyhrNC9ZwdT0f8jc4dQQeDQ7G4m0f2QCLPJiMTTO6wfDmRmj/pW0PsUvIcA==",
      "dev": true
    },
    "@webassemblyjs/helper-numbers": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/helper-numbers/-/helper-numbers-1.11.1.tgz",
      "integrity": "sha512-vDkbxiB8zfnPdNK9Rajcey5C0w+QJugEglN0of+kmO8l7lDb77AnlKYQF7aarZuCrv+l0UvqL+68gSDr3k9LPQ==",
      "dev": true,
      "requires": {
        "@webassemblyjs/floating-point-hex-parser": "1.11.1",
        "@webassemblyjs/helper-api-error": "1.11.1",
        "@xtuc/long": "4.2.2"
      }
    },
    "@webassemblyjs/helper-wasm-bytecode": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/helper-wasm-bytecode/-/helper-wasm-bytecode-1.11.1.tgz",
      "integrity": "sha512-PvpoOGiJwXeTrSf/qfudJhwlvDQxFgelbMqtq52WWiXC6Xgg1IREdngmPN3bs4RoO83PnL/nFrxucXj1+BX62Q==",
      "dev": true
    },
    "@webassemblyjs/helper-wasm-section": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/helper-wasm-section/-/helper-wasm-section-1.11.1.tgz",
      "integrity": "sha512-10P9No29rYX1j7F3EVPX3JvGPQPae+AomuSTPiF9eBQeChHI6iqjMIwR9JmOJXwpnn/oVGDk7I5IlskuMwU/pg==",
      "dev": true,
      "requires": {
        "@webassemblyjs/ast": "1.11.1",
        "@webassemblyjs/helper-buffer": "1.11.1",
        "@webassemblyjs/helper-wasm-bytecode": "1.11.1",
        "@webassemblyjs/wasm-gen": "1.11.1"
      }
    },
    "@webassemblyjs/ieee754": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/ieee754/-/ieee754-1.11.1.tgz",
      "integrity": "sha512-hJ87QIPtAMKbFq6CGTkZYJivEwZDbQUgYd3qKSadTNOhVY7p+gfP6Sr0lLRVTaG1JjFj+r3YchoqRYxNH3M0GQ==",
      "dev": true,
      "requires": {
        "@xtuc/ieee754": "^1.2.0"
      }
    },
    "@webassemblyjs/leb128": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/leb128/-/leb128-1.11.1.tgz",
      "integrity": "sha512-BJ2P0hNZ0u+Th1YZXJpzW6miwqQUGcIHT1G/sf72gLVD9DZ5AdYTqPNbHZh6K1M5VmKvFXwGSWZADz+qBWxeRw==",
      "dev": true,
      "requires": {
        "@xtuc/long": "4.2.2"
      }
    },
    "@webassemblyjs/utf8": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/utf8/-/utf8-1.11.1.tgz",
      "integrity": "sha512-9kqcxAEdMhiwQkHpkNiorZzqpGrodQQ2IGrHHxCy+Ozng0ofyMA0lTqiLkVs1uzTRejX+/O0EOT7KxqVPuXosQ==",
      "dev": true
    },
    "@webassemblyjs/wasm-edit": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/wasm-edit/-/wasm-edit-1.11.1.tgz",
      "integrity": "sha512-g+RsupUC1aTHfR8CDgnsVRVZFJqdkFHpsHMfJuWQzWU3tvnLC07UqHICfP+4XyL2tnr1amvl1Sdp06TnYCmVkA==",
      "dev": true,
      "requires": {
        "@webassemblyjs/ast": "1.11.1",
        "@webassemblyjs/helper-buffer": "1.11.1",
        "@webassemblyjs/helper-wasm-bytecode": "1.11.1",
        "@webassemblyjs/helper-wasm-section": "1.11.1",
        "@webassemblyjs/wasm-gen": "1.11.1",
        "@webassemblyjs/wasm-opt": "1.11.1",
        "@webassemblyjs/wasm-parser": "1.11.1",
        "@webassemblyjs/wast-printer": "1.11.1"
      }
    },
    "@webassemblyjs/wasm-gen": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/wasm-gen/-/wasm-gen-1.11.1.tgz",
      "integrity": "sha512-F7QqKXwwNlMmsulj6+O7r4mmtAlCWfO/0HdgOxSklZfQcDu0TpLiD1mRt/zF25Bk59FIjEuGAIyn5ei4yMfLhA==",
      "dev": true,
      "requires": {
        "@webassemblyjs/ast": "1.11.1",
        "@webassemblyjs/helper-wasm-bytecode": "1.11.1",
        "@webassemblyjs/ieee754": "1.11.1",
        "@webassemblyjs/leb128": "1.11.1",
        "@webassemblyjs/utf8": "1.11.1"
      }
    },
    "@webassemblyjs/wasm-opt": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/wasm-opt/-/wasm-opt-1.11.1.tgz",
      "integrity": "sha512-VqnkNqnZlU5EB64pp1l7hdm3hmQw7Vgqa0KF/KCNO9sIpI6Fk6brDEiX+iCOYrvMuBWDws0NkTOxYEb85XQHHw==",
      "dev": true,
      "requires": {
        "@webassemblyjs/ast": "1.11.1",
        "@webassemblyjs/helper-buffer": "1.11.1",
        "@webassemblyjs/wasm-gen": "1.11.1",
        "@webassemblyjs/wasm-parser": "1.11.1"
      }
    },
    "@webassemblyjs/wasm-parser": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/wasm-parser/-/wasm-parser-1.11.1.tgz",
      "integrity": "sha512-rrBujw+dJu32gYB7/Lup6UhdkPx9S9SnobZzRVL7VcBH9Bt9bCBLEuX/YXOOtBsOZ4NQrRykKhffRWHvigQvOA==",
      "dev": true,
      "requires": {
        "@webassemblyjs/ast": "1.11.1",
        "@webassemblyjs/helper-api-error": "1.11.1",
        "@webassemblyjs/helper-wasm-bytecode": "1.11.1",
        "@webassemblyjs/ieee754": "1.11.1",
        "@webassemblyjs/leb128": "1.11.1",
        "@webassemblyjs/utf8": "1.11.1"
      }
    },
    "@webassemblyjs/wast-printer": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/@webassemblyjs/wast-printer/-/wast-printer-1.11.1.tgz",
      "integrity": "sha512-IQboUWM4eKzWW+N/jij2sRatKMh99QEelo3Eb2q0qXkvPRISAj8Qxtmw5itwqK+TTkBuUIE45AxYPToqPtL5gg==",
      "dev": true,
      "requires": {
        "@webassemblyjs/ast": "1.11.1",
        "@xtuc/long": "4.2.2"
      }
    },
    "@xtuc/ieee754": {
      "version": "1.2.0",
      "resolved": "https://registry.npmjs.org/@xtuc/ieee754/-/ieee754-1.2.0.tgz",
      "integrity": "sha512-DX8nKgqcGwsc0eJSqYt5lwP4DH5FlHnmuWWBRy7X0NcaGR0ZtuyeESgMwTYVEtxmsNGY+qit4QYT/MIYTOTPeA==",
      "dev": true
    },
    "@xtuc/long": {
      "version": "4.2.2",
      "resolved": "https://registry.npmjs.org/@xtuc/long/-/long-4.2.2.tgz",
      "integrity": "sha512-NuHqBY1PB/D8xU6s/thBgOAiAP7HOYDQ32+BFZILJ8ivkUkAHQnWfn6WhL79Owj1qmUnoN/YPhktdIoucipkAQ==",
      "dev": true
    },
    "@yarnpkg/lockfile": {
      "version": "1.1.0",
      "resolved": "https://registry.npmjs.org/@yarnpkg/lockfile/-/lockfile-1.1.0.tgz",
      "integrity": "sha512-GpSwvyXOcOOlV70vbnzjj4fW5xW/FdUF6nQEt1ENy7m4ZCczi1+/buVUPAqmGfqznsORNFzUMjctTIp8a9tuCQ==",
      "dev": true
    },
    "abab": {
      "version": "2.0.5",
      "resolved": "https://registry.npmjs.org/abab/-/abab-2.0.5.tgz",
      "integrity": "sha512-9IK9EadsbHo6jLWIpxpR6pL0sazTXV6+SQv25ZB+F7Bj9mJNaOc4nCRabwd5M/JwmUa8idz6Eci6eKfJryPs6Q==",
      "dev": true
    },
    "abbrev": {
      "version": "1.1.1",
      "resolved": "https://registry.npmjs.org/abbrev/-/abbrev-1.1.1.tgz",
      "integrity": "sha512-nne9/IiQ/hzIhY6pdDnbBtz7DjPTKrY00P/zvPSm5pOFkl6xuGrGnXn/VtTNNfNtAfZ9/1RtehkszU9qcTii0Q==",
      "dev": true
    },
    "accepts": {
      "version": "1.3.7",
      "resolved": "https://registry.npmjs.org/accepts/-/accepts-1.3.7.tgz",
      "integrity": "sha512-Il80Qs2WjYlJIBNzNkK6KYqlVMTbZLXgHx2oT0pU/fjRHyEp+PEfEPY0R3WCwAGVOtauxh1hOxNgIf5bv7dQpA==",
      "requires": {
        "mime-types": "~2.1.24",
        "negotiator": "0.6.2"
      },
      "dependencies": {
        "negotiator": {
          "version": "0.6.2",
          "resolved": "https://registry.npmjs.org/negotiator/-/negotiator-0.6.2.tgz",
          "integrity": "sha512-hZXc7K2e+PgeI1eDBe/10Ard4ekbfrrqG8Ep+8Jmf4JID2bNg7NvCPOZN+kfF574pFQI7mum2AUqDidoKqcTOw=="
        }
      }
    },
    "acorn": {
      "version": "8.7.0",
      "resolved": "https://registry.npmjs.org/acorn/-/acorn-8.7.0.tgz",
      "integrity": "sha512-V/LGr1APy+PXIwKebEWrkZPwoeoF+w1jiOBUmuxuiUIaOHtob8Qc9BTrYo7VuI5fR8tqsy+buA2WFooR5olqvQ==",
      "dev": true
    },
    "acorn-import-assertions": {
      "version": "1.8.0",
      "resolved": "https://registry.npmjs.org/acorn-import-assertions/-/acorn-import-assertions-1.8.0.tgz",
      "integrity": "sha512-m7VZ3jwz4eK6A4Vtt8Ew1/mNbP24u0FhdyfA7fSvnJR6LMdfOYnmuIrrJAgrYfYJ10F/otaHTtrtrtmHdMNzEw==",
      "dev": true,
      "requires": {}
    },
    "adjust-sourcemap-loader": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/adjust-sourcemap-loader/-/adjust-sourcemap-loader-4.0.0.tgz",
      "integrity": "sha512-OXwN5b9pCUXNQHJpwwD2qP40byEmSgzj8B4ydSN0uMNYWiFmJ6x6KwUllMmfk8Rwu/HJDFR7U8ubsWBoN0Xp0A==",
      "dev": true,
      "requires": {
        "loader-utils": "^2.0.0",
        "regex-parser": "^2.2.11"
      },
      "dependencies": {
        "loader-utils": {
          "version": "2.0.2",
          "resolved": "https://registry.npmjs.org/loader-utils/-/loader-utils-2.0.2.tgz",
          "integrity": "sha512-TM57VeHptv569d/GKh6TAYdzKblwDNiumOdkFnejjD0XwTH87K90w3O7AiJRqdQoXygvi1VQTJTLGhJl7WqA7A==",
          "dev": true,
          "requires": {
            "big.js": "^5.2.2",
            "emojis-list": "^3.0.0",
            "json5": "^2.1.2"
          }
        }
      }
    },
    "agent-base": {
      "version": "6.0.2",
      "resolved": "https://registry.npmjs.org/agent-base/-/agent-base-6.0.2.tgz",
      "integrity": "sha512-RZNwNclF7+MS/8bDg70amg32dyeZGZxiDuQmZxKLAlQjr3jGyLx+4Kkk58UO7D2QdgFIQCovuSuZESne6RG6XQ==",
      "dev": true,
      "requires": {
        "debug": "4"
      }
    },
    "agentkeepalive": {
      "version": "4.2.0",
      "resolved": "https://registry.npmjs.org/agentkeepalive/-/agentkeepalive-4.2.0.tgz",
      "integrity": "sha512-0PhAp58jZNw13UJv7NVdTGb0ZcghHUb3DrZ046JiiJY/BOaTTpbwdHq2VObPCBV8M2GPh7sgrJ3AQ8Ey468LJw==",
      "dev": true,
      "requires": {
        "debug": "^4.1.0",
        "depd": "^1.1.2",
        "humanize-ms": "^1.2.1"
      }
    },
    "aggregate-error": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/aggregate-error/-/aggregate-error-3.1.0.tgz",
      "integrity": "sha512-4I7Td01quW/RpocfNayFdFVk1qSuoh0E7JrbRJ16nH01HhKFQ88INq9Sd+nd72zqRySlr9BmDA8xlEJ6vJMrYA==",
      "dev": true,
      "requires": {
        "clean-stack": "^2.0.0",
        "indent-string": "^4.0.0"
      }
    },
    "ajv": {
      "version": "8.8.2",
      "resolved": "https://registry.npmjs.org/ajv/-/ajv-8.8.2.tgz",
      "integrity": "sha512-x9VuX+R/jcFj1DHo/fCp99esgGDWiHENrKxaCENuCxpoMCmAt/COCGVDwA7kleEpEzJjDnvh3yGoOuLu0Dtllw==",
      "dev": true,
      "requires": {
        "fast-deep-equal": "^3.1.1",
        "json-schema-traverse": "^1.0.0",
        "require-from-string": "^2.0.2",
        "uri-js": "^4.2.2"
      }
    },
    "ajv-formats": {
      "version": "2.1.1",
      "resolved": "https://registry.npmjs.org/ajv-formats/-/ajv-formats-2.1.1.tgz",
      "integrity": "sha512-Wx0Kx52hxE7C18hkMEggYlEifqWZtYaRgouJor+WMdPnQyEK13vgEWyVNup7SoeeoLMsr4kf5h6dOW11I15MUA==",
      "dev": true,
      "requires": {
        "ajv": "^8.0.0"
      }
    },
    "ajv-keywords": {
      "version": "5.1.0",
      "resolved": "https://registry.npmjs.org/ajv-keywords/-/ajv-keywords-5.1.0.tgz",
      "integrity": "sha512-YCS/JNFAUyr5vAuhk1DWm1CBxRHW9LbJ2ozWeemrIqpbsqKjHVxYPyi5GC0rjZIT5JxJ3virVTS8wk4i/Z+krw==",
      "dev": true,
      "requires": {
        "fast-deep-equal": "^3.1.3"
      }
    },
    "ansi-align": {
      "version": "3.0.1",
      "resolved": "https://registry.npmjs.org/ansi-align/-/ansi-align-3.0.1.tgz",
      "integrity": "sha512-IOfwwBF5iczOjp/WeY4YxyjqAFMQoZufdQWDd19SEExbVLNXqvpzSJ/M7Za4/sCPmQ0+GRquoA7bGcINcxew6w==",
      "requires": {
        "string-width": "^4.1.0"
      }
    },
    "ansi-colors": {
      "version": "4.1.1",
      "resolved": "https://registry.npmjs.org/ansi-colors/-/ansi-colors-4.1.1.tgz",
      "integrity": "sha512-JoX0apGbHaUJBNl6yF+p6JAFYZ666/hhCGKN5t9QFjbJQKUU/g8MNbFDbvfrgKXvI1QpZplPOnwIo99lX/AAmA==",
      "dev": true
    },
    "ansi-escapes": {
      "version": "4.3.2",
      "resolved": "https://registry.npmjs.org/ansi-escapes/-/ansi-escapes-4.3.2.tgz",
      "integrity": "sha512-gKXj5ALrKWQLsYG9jlTRmR/xKluxHV+Z9QEwNIgCfM1/uwPMCuzVVnh5mwTd+OuBZcwSIMbqssNWRm1lE51QaQ==",
      "dev": true,
      "requires": {
        "type-fest": "^0.21.3"
      }
    },
    "ansi-html-community": {
      "version": "0.0.8",
      "resolved": "https://registry.npmjs.org/ansi-html-community/-/ansi-html-community-0.0.8.tgz",
      "integrity": "sha512-1APHAyr3+PCamwNw3bXCPp4HFLONZt/yIH0sZp0/469KWNTEy+qN5jQ3GVX6DMZ1UXAi34yVwtTeaG/HpBuuzw==",
      "dev": true
    },
    "ansi-regex": {
      "version": "5.0.1",
      "resolved": "https://registry.npmjs.org/ansi-regex/-/ansi-regex-5.0.1.tgz",
      "integrity": "sha512-quJQXlTSUGL2LH9SUXo8VwsY4soanhgo6LNSm84E1LBcE8s3O0wpdiRzyR9z/ZZJMlMWv37qOOb9pdJlMUEKFQ=="
    },
    "ansi-styles": {
      "version": "3.2.1",
      "resolved": "https://registry.npmjs.org/ansi-styles/-/ansi-styles-3.2.1.tgz",
      "integrity": "sha512-VT0ZI6kZRdTh8YyJw3SMbYm/u+NqfsAxEpWO0Pf9sq8/e94WxxOpPKx9FR1FlyCtOVDNOQ+8ntlqFxiRc+r5qA==",
      "dev": true,
      "requires": {
        "color-convert": "^1.9.0"
      }
    },
    "anymatch": {
      "version": "3.1.2",
      "resolved": "https://registry.npmjs.org/anymatch/-/anymatch-3.1.2.tgz",
      "integrity": "sha512-P43ePfOAIupkguHUycrc4qJ9kz8ZiuOUijaETwX7THt0Y/GNK7v0aa8rY816xWjZ7rJdA5XdMcpVFTKMq+RvWg==",
      "dev": true,
      "requires": {
        "normalize-path": "^3.0.0",
        "picomatch": "^2.0.4"
      }
    },
    "aproba": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/aproba/-/aproba-2.0.0.tgz",
      "integrity": "sha512-lYe4Gx7QT+MKGbDsA+Z+he/Wtef0BiwDOlK/XkBrdfsh9J/jPPXbX0tE9x9cl27Tmu5gg3QUbUrQYa/y+KOHPQ==",
      "dev": true
    },
    "are-we-there-yet": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/are-we-there-yet/-/are-we-there-yet-2.0.0.tgz",
      "integrity": "sha512-Ci/qENmwHnsYo9xKIcUJN5LeDKdJ6R1Z1j9V/J5wyq8nh/mYPEpIKJbBZXtZjG04HiK7zV/p6Vs9952MrMeUIw==",
      "dev": true,
      "requires": {
        "delegates": "^1.0.0",
        "readable-stream": "^3.6.0"
      }
    },
    "argparse": {
      "version": "1.0.10",
      "resolved": "https://registry.npmjs.org/argparse/-/argparse-1.0.10.tgz",
      "integrity": "sha512-o5Roy6tNG4SL/FOkCAN6RzjiakZS25RLYFrcMttJqbdd8BWrnA+fGz57iN5Pb06pvBGvl5gQ0B48dJlslXvoTg==",
      "dev": true,
      "requires": {
        "sprintf-js": "~1.0.2"
      }
    },
    "array-flatten": {
      "version": "2.1.2",
      "resolved": "https://registry.npmjs.org/array-flatten/-/array-flatten-2.1.2.tgz",
      "integrity": "sha512-hNfzcOV8W4NdualtqBFPyVO+54DSJuZGY9qT4pRroB6S9e3iiido2ISIC5h9R2sPJ8H3FHCIiEnsv1lPXO3KtQ==",
      "dev": true
    },
    "array-union": {
      "version": "3.0.1",
      "resolved": "https://registry.npmjs.org/array-union/-/array-union-3.0.1.tgz",
      "integrity": "sha512-1OvF9IbWwaeiM9VhzYXVQacMibxpXOMYVNIvMtKRyX9SImBXpKcFr8XvFDeEslCyuH/t6KRt7HEO94AlP8Iatw==",
      "dev": true
    },
    "async": {
      "version": "2.6.3",
      "resolved": "https://registry.npmjs.org/async/-/async-2.6.3.tgz",
      "integrity": "sha512-zflvls11DCy+dQWzTW2dzuilv8Z5X/pjfmZOWba6TNIVDm+2UDaJmXSOXlasHKfNBs8oo3M0aT50fDEWfKZjXg==",
      "dev": true,
      "requires": {
        "lodash": "^4.17.14"
      }
    },
    "atob": {
      "version": "2.1.2",
      "resolved": "https://registry.npmjs.org/atob/-/atob-2.1.2.tgz",
      "integrity": "sha512-Wm6ukoaOGJi/73p/cl2GvLjTI5JM1k/O14isD73YML8StrH/7/lRFgmg8nICZgD3bZZvjwCGxtMOD3wWNAu8cg==",
      "dev": true
    },
    "autoprefixer": {
      "version": "10.4.2",
      "resolved": "https://registry.npmjs.org/autoprefixer/-/autoprefixer-10.4.2.tgz",
      "integrity": "sha512-9fOPpHKuDW1w/0EKfRmVnxTDt8166MAnLI3mgZ1JCnhNtYWxcJ6Ud5CO/AVOZi/AvFa8DY9RTy3h3+tFBlrrdQ==",
      "dev": true,
      "requires": {
        "browserslist": "^4.19.1",
        "caniuse-lite": "^1.0.30001297",
        "fraction.js": "^4.1.2",
        "normalize-range": "^0.1.2",
        "picocolors": "^1.0.0",
        "postcss-value-parser": "^4.2.0"
      }
    },
    "babel-loader": {
      "version": "8.2.3",
      "resolved": "https://registry.npmjs.org/babel-loader/-/babel-loader-8.2.3.tgz",
      "integrity": "sha512-n4Zeta8NC3QAsuyiizu0GkmRcQ6clkV9WFUnUf1iXP//IeSKbWjofW3UHyZVwlOB4y039YQKefawyTn64Zwbuw==",
      "dev": true,
      "requires": {
        "find-cache-dir": "^3.3.1",
        "loader-utils": "^1.4.0",
        "make-dir": "^3.1.0",
        "schema-utils": "^2.6.5"
      },
      "dependencies": {
        "json5": {
          "version": "1.0.1",
          "resolved": "https://registry.npmjs.org/json5/-/json5-1.0.1.tgz",
          "integrity": "sha512-aKS4WQjPenRxiQsC93MNfjx+nbF4PAdYzmd/1JIj8HYzqfbu86beTuNgXDzPknWk0n0uARlyewZo4s++ES36Ow==",
          "dev": true,
          "requires": {
            "minimist": "^1.2.0"
          }
        },
        "loader-utils": {
          "version": "1.4.0",
          "resolved": "https://registry.npmjs.org/loader-utils/-/loader-utils-1.4.0.tgz",
          "integrity": "sha512-qH0WSMBtn/oHuwjy/NucEgbx5dbxxnxup9s4PVXJUDHZBQY+s0NWA9rJf53RBnQZxfch7euUui7hpoAPvALZdA==",
          "dev": true,
          "requires": {
            "big.js": "^5.2.2",
            "emojis-list": "^3.0.0",
            "json5": "^1.0.1"
          }
        }
      }
    },
    "babel-plugin-dynamic-import-node": {
      "version": "2.3.3",
      "resolved": "https://registry.npmjs.org/babel-plugin-dynamic-import-node/-/babel-plugin-dynamic-import-node-2.3.3.tgz",
      "integrity": "sha512-jZVI+s9Zg3IqA/kdi0i6UDCybUI3aSBLnglhYbSSjKlV7yF1F/5LWv8MakQmvYpnbJDS6fcBL2KzHSxNCMtWSQ==",
      "dev": true,
      "requires": {
        "object.assign": "^4.1.0"
      }
    },
    "babel-plugin-istanbul": {
      "version": "6.1.1",
      "resolved": "https://registry.npmjs.org/babel-plugin-istanbul/-/babel-plugin-istanbul-6.1.1.tgz",
      "integrity": "sha512-Y1IQok9821cC9onCx5otgFfRm7Lm+I+wwxOx738M/WLPZ9Q42m4IG5W0FNX8WLL2gYMZo3JkuXIH2DOpWM+qwA==",
      "dev": true,
      "requires": {
        "@babel/helper-plugin-utils": "^7.0.0",
        "@istanbuljs/load-nyc-config": "^1.0.0",
        "@istanbuljs/schema": "^0.1.2",
        "istanbul-lib-instrument": "^5.0.4",
        "test-exclude": "^6.0.0"
      }
    },
    "babel-plugin-polyfill-corejs2": {
      "version": "0.3.1",
      "resolved": "https://registry.npmjs.org/babel-plugin-polyfill-corejs2/-/babel-plugin-polyfill-corejs2-0.3.1.tgz",
      "integrity": "sha512-v7/T6EQcNfVLfcN2X8Lulb7DjprieyLWJK/zOWH5DUYcAgex9sP3h25Q+DLsX9TloXe3y1O8l2q2Jv9q8UVB9w==",
      "dev": true,
      "requires": {
        "@babel/compat-data": "^7.13.11",
        "@babel/helper-define-polyfill-provider": "^0.3.1",
        "semver": "^6.1.1"
      },
      "dependencies": {
        "semver": {
          "version": "6.3.0",
          "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.0.tgz",
          "integrity": "sha512-b39TBaTSfV6yBrapU89p5fKekE2m/NwnDocOVruQFS1/veMgdzuPcnOM34M6CwxW8jH/lxEa5rBoDeUwu5HHTw==",
          "dev": true
        }
      }
    },
    "babel-plugin-polyfill-corejs3": {
      "version": "0.4.0",
      "resolved": "https://registry.npmjs.org/babel-plugin-polyfill-corejs3/-/babel-plugin-polyfill-corejs3-0.4.0.tgz",
      "integrity": "sha512-YxFreYwUfglYKdLUGvIF2nJEsGwj+RhWSX/ije3D2vQPOXuyMLMtg/cCGMDpOA7Nd+MwlNdnGODbd2EwUZPlsw==",
      "dev": true,
      "requires": {
        "@babel/helper-define-polyfill-provider": "^0.3.0",
        "core-js-compat": "^3.18.0"
      }
    },
    "babel-plugin-polyfill-regenerator": {
      "version": "0.3.1",
      "resolved": "https://registry.npmjs.org/babel-plugin-polyfill-regenerator/-/babel-plugin-polyfill-regenerator-0.3.1.tgz",
      "integrity": "sha512-Y2B06tvgHYt1x0yz17jGkGeeMr5FeKUu+ASJ+N6nB5lQ8Dapfg42i0OVrf8PNGJ3zKL4A23snMi1IRwrqqND7A==",
      "dev": true,
      "requires": {
        "@babel/helper-define-polyfill-provider": "^0.3.1"
      }
    },
    "balanced-match": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/balanced-match/-/balanced-match-1.0.2.tgz",
      "integrity": "sha512-3oSeUO0TMV67hN1AmbXsK4yaqU7tjiHlbxRDZOpH0KW9+CeX4bRAaX0Anxt0tx2MrpRpWwQaPwIlISEJhYU5Pw==",
      "dev": true
    },
    "base64-js": {
      "version": "1.5.1",
      "resolved": "https://registry.npmjs.org/base64-js/-/base64-js-1.5.1.tgz",
      "integrity": "sha512-AKpaYlHn8t4SVbOHCy+b5+KKgvR4vrsD8vbvrbiQJps7fKDTkjkDry6ji0rUJjC0kzbNePLwzxq8iypo41qeWA==",
      "dev": true
    },
    "base64id": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/base64id/-/base64id-2.0.0.tgz",
      "integrity": "sha512-lGe34o6EHj9y3Kts9R4ZYs/Gr+6N7MCaMlIFA3F1R2O5/m7K06AxfSeO5530PEERE6/WyEg3lsuyw4GHlPZHog==",
      "dev": true
    },
    "basic-auth": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/basic-auth/-/basic-auth-2.0.1.tgz",
      "integrity": "sha512-NF+epuEdnUYVlGuhaxbbq+dvJttwLnGY+YixlXlME5KpQ5W3CnXA5cVTneY3SPbPDRkcjMbifrwmFYcClgOZeg==",
      "requires": {
        "safe-buffer": "5.1.2"
      }
    },
    "batch": {
      "version": "0.6.1",
      "resolved": "https://registry.npmjs.org/batch/-/batch-0.6.1.tgz",
      "integrity": "sha1-3DQxT05nkxgJP8dgJyUl+UvyXBY=",
      "dev": true
    },
    "big.js": {
      "version": "5.2.2",
      "resolved": "https://registry.npmjs.org/big.js/-/big.js-5.2.2.tgz",
      "integrity": "sha512-vyL2OymJxmarO8gxMr0mhChsO9QGwhynfuu4+MHTAW6czfq9humCB7rKpUjDd9YUiDPU4mzpyupFSvOClAwbmQ==",
      "dev": true
    },
    "binary-extensions": {
      "version": "2.2.0",
      "resolved": "https://registry.npmjs.org/binary-extensions/-/binary-extensions-2.2.0.tgz",
      "integrity": "sha512-jDctJ/IVQbZoJykoeHbhXpOlNBqGNcwXJKJog42E5HDPUwQTSdjCHdihjj0DlnheQ7blbT6dHOafNAiS8ooQKA==",
      "dev": true
    },
    "bl": {
      "version": "4.1.0",
      "resolved": "https://registry.npmjs.org/bl/-/bl-4.1.0.tgz",
      "integrity": "sha512-1W07cM9gS6DcLperZfFSj+bWLtaPGSOHWhPiGzXmvVJbRLdG82sH/Kn8EtW1VqWVA54AKf2h5k5BbnIbwF3h6w==",
      "dev": true,
      "requires": {
        "buffer": "^5.5.0",
        "inherits": "^2.0.4",
        "readable-stream": "^3.4.0"
      }
    },
    "body-parser": {
      "version": "1.19.1",
      "resolved": "https://registry.npmjs.org/body-parser/-/body-parser-1.19.1.tgz",
      "integrity": "sha512-8ljfQi5eBk8EJfECMrgqNGWPEY5jWP+1IzkzkGdFFEwFQZZyaZ21UqdaHktgiMlH0xLHqIFtE/u2OYE5dOtViA==",
      "requires": {
        "bytes": "3.1.1",
        "content-type": "~1.0.4",
        "debug": "2.6.9",
        "depd": "~1.1.2",
        "http-errors": "1.8.1",
        "iconv-lite": "0.4.24",
        "on-finished": "~2.3.0",
        "qs": "6.9.6",
        "raw-body": "2.4.2",
        "type-is": "~1.6.18"
      },
      "dependencies": {
        "debug": {
          "version": "2.6.9",
          "resolved": "https://registry.npmjs.org/debug/-/debug-2.6.9.tgz",
          "integrity": "sha512-bC7ElrdJaJnPbAP+1EotYvqZsb3ecl5wi6Bfi6BJTUcNowp6cvspg0jXznRTKDjm/E7AdgFBVeAPVMNcKGsHMA==",
          "requires": {
            "ms": "2.0.0"
          }
        },
        "ms": {
          "version": "2.0.0",
          "resolved": "https://registry.npmjs.org/ms/-/ms-2.0.0.tgz",
          "integrity": "sha1-VgiurfwAvmwpAd9fmGF4jeDVl8g="
        }
      }
    },
    "bonjour": {
      "version": "3.5.0",
      "resolved": "https://registry.npmjs.org/bonjour/-/bonjour-3.5.0.tgz",
      "integrity": "sha1-jokKGD2O6aI5OzhExpGkK897yfU=",
      "dev": true,
      "requires": {
        "array-flatten": "^2.1.0",
        "deep-equal": "^1.0.1",
        "dns-equal": "^1.0.0",
        "dns-txt": "^2.0.2",
        "multicast-dns": "^6.0.1",
        "multicast-dns-service-types": "^1.1.0"
      }
    },
    "boolbase": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/boolbase/-/boolbase-1.0.0.tgz",
      "integrity": "sha1-aN/1++YMUes3cl6p4+0xDcwed24=",
      "dev": true
    },
    "bootstrap": {
      "version": "5.1.3",
      "resolved": "https://registry.npmjs.org/bootstrap/-/bootstrap-5.1.3.tgz",
      "integrity": "sha512-fcQztozJ8jToQWXxVuEyXWW+dSo8AiXWKwiSSrKWsRB/Qt+Ewwza+JWoLKiTuQLaEPhdNAJ7+Dosc9DOIqNy7Q==",
      "requires": {}
    },
    "boxen": {
      "version": "5.1.2",
      "resolved": "https://registry.npmjs.org/boxen/-/boxen-5.1.2.tgz",
      "integrity": "sha512-9gYgQKXx+1nP8mP7CzFyaUARhg7D3n1dF/FnErWmu9l6JvGpNUN278h0aSb+QjoiKSWG+iZ3uHrcqk0qrY9RQQ==",
      "requires": {
        "ansi-align": "^3.0.0",
        "camelcase": "^6.2.0",
        "chalk": "^4.1.0",
        "cli-boxes": "^2.2.1",
        "string-width": "^4.2.2",
        "type-fest": "^0.20.2",
        "widest-line": "^3.1.0",
        "wrap-ansi": "^7.0.0"
      },
      "dependencies": {
        "ansi-styles": {
          "version": "4.3.0",
          "resolved": "https://registry.npmjs.org/ansi-styles/-/ansi-styles-4.3.0.tgz",
          "integrity": "sha512-zbB9rCJAT1rbjiVDb2hqKFHNYLxgtk8NURxZ3IZwD3F6NtxbXZQCnnSi1Lkx+IDohdPlFp222wVALIheZJQSEg==",
          "requires": {
            "color-convert": "^2.0.1"
          }
        },
        "camelcase": {
          "version": "6.3.0",
          "resolved": "https://registry.npmjs.org/camelcase/-/camelcase-6.3.0.tgz",
          "integrity": "sha512-Gmy6FhYlCY7uOElZUSbxo2UCDH8owEk996gkbrpsgGtrJLM3J7jGxl9Ic7Qwwj4ivOE5AWZWRMecDdF7hqGjFA=="
        },
        "chalk": {
          "version": "4.1.2",
          "resolved": "https://registry.npmjs.org/chalk/-/chalk-4.1.2.tgz",
          "integrity": "sha512-oKnbhFyRIXpUuez8iBMmyEa4nbj4IOQyuhc/wy9kY7/WVPcwIO9VA668Pu8RkO7+0G76SLROeyw9CpQ061i4mA==",
          "requires": {
            "ansi-styles": "^4.1.0",
            "supports-color": "^7.1.0"
          }
        },
        "color-convert": {
          "version": "2.0.1",
          "resolved": "https://registry.npmjs.org/color-convert/-/color-convert-2.0.1.tgz",
          "integrity": "sha512-RRECPsj7iu/xb5oKYcsFHSppFNnsj/52OVTRKb4zP5onXwVF3zVmmToNcOfGC+CRDpfK/U584fMg38ZHCaElKQ==",
          "requires": {
            "color-name": "~1.1.4"
          }
        },
        "color-name": {
          "version": "1.1.4",
          "resolved": "https://registry.npmjs.org/color-name/-/color-name-1.1.4.tgz",
          "integrity": "sha512-dOy+3AuW3a2wNbZHIuMZpTcgjGuLU/uBL/ubcZF9OXbDo8ff4O8yVp5Bf0efS8uEoYo5q4Fx7dY9OgQGXgAsQA=="
        },
        "has-flag": {
          "version": "4.0.0",
          "resolved": "https://registry.npmjs.org/has-flag/-/has-flag-4.0.0.tgz",
          "integrity": "sha512-EykJT/Q1KjTWctppgIAgfSO0tKVuZUjhgMr17kqTumMl6Afv3EISleU7qZUzoXDFTAHTDC4NOoG/ZxU3EvlMPQ=="
        },
        "supports-color": {
          "version": "7.2.0",
          "resolved": "https://registry.npmjs.org/supports-color/-/supports-color-7.2.0.tgz",
          "integrity": "sha512-qpCAvRl9stuOHveKsn7HncJRvv501qIacKzQlO/+Lwxc9+0q2wLyv4Dfvt80/DPn2pqOBsJdDiogXGR9+OvwRw==",
          "requires": {
            "has-flag": "^4.0.0"
          }
        },
        "type-fest": {
          "version": "0.20.2",
          "resolved": "https://registry.npmjs.org/type-fest/-/type-fest-0.20.2.tgz",
          "integrity": "sha512-Ne+eE4r0/iWnpAxD852z3A+N0Bt5RN//NjJwRd2VFHEmrywxf5vsZlh4R6lixl6B+wz/8d+maTSAkN1FIkI3LQ=="
        }
      }
    },
    "brace-expansion": {
      "version": "1.1.11",
      "resolved": "https://registry.npmjs.org/brace-expansion/-/brace-expansion-1.1.11.tgz",
      "integrity": "sha512-iCuPHDFgrHX7H2vEI/5xpz07zSHB00TpugqhmYtVmMO6518mCuRMoOYFldEBl0g187ufozdaHgWKcYFb61qGiA==",
      "dev": true,
      "requires": {
        "balanced-match": "^1.0.0",
        "concat-map": "0.0.1"
      }
    },
    "braces": {
      "version": "3.0.2",
      "resolved": "https://registry.npmjs.org/braces/-/braces-3.0.2.tgz",
      "integrity": "sha512-b8um+L1RzM3WDSzvhm6gIz1yfTbBt6YTlcEKAvsmqCZZFw46z626lVj9j1yEPW33H5H+lBQpZMP1k8l+78Ha0A==",
      "dev": true,
      "requires": {
        "fill-range": "^7.0.1"
      }
    },
    "browserslist": {
      "version": "4.19.1",
      "resolved": "https://registry.npmjs.org/browserslist/-/browserslist-4.19.1.tgz",
      "integrity": "sha512-u2tbbG5PdKRTUoctO3NBD8FQ5HdPh1ZXPHzp1rwaa5jTc+RV9/+RlWiAIKmjRPQF+xbGM9Kklj5bZQFa2s/38A==",
      "dev": true,
      "requires": {
        "caniuse-lite": "^1.0.30001286",
        "electron-to-chromium": "^1.4.17",
        "escalade": "^3.1.1",
        "node-releases": "^2.0.1",
        "picocolors": "^1.0.0"
      }
    },
    "buffer": {
      "version": "5.7.1",
      "resolved": "https://registry.npmjs.org/buffer/-/buffer-5.7.1.tgz",
      "integrity": "sha512-EHcyIPBQ4BSGlvjB16k5KgAJ27CIsHY/2JBmCRReo48y9rQ3MaUzWX3KVlBa4U7MyX02HdVj0K7C3WaB3ju7FQ==",
      "dev": true,
      "requires": {
        "base64-js": "^1.3.1",
        "ieee754": "^1.1.13"
      }
    },
    "buffer-from": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/buffer-from/-/buffer-from-1.1.2.tgz",
      "integrity": "sha512-E+XQCRwSbaaiChtv6k6Dwgc+bx+Bs6vuKJHHl5kox/BaKbhiXzqQOwK4cO22yElGp2OCmjwVhT3HmxgyPGnJfQ==",
      "dev": true
    },
    "buffer-indexof": {
      "version": "1.1.1",
      "resolved": "https://registry.npmjs.org/buffer-indexof/-/buffer-indexof-1.1.1.tgz",
      "integrity": "sha512-4/rOEg86jivtPTeOUUT61jJO1Ya1TrR/OkqCSZDyq84WJh3LuuiphBYJN+fm5xufIk4XAFcEwte/8WzC8If/1g==",
      "dev": true
    },
    "builtins": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/builtins/-/builtins-1.0.3.tgz",
      "integrity": "sha1-y5T662HIaWRR2zZTThQi+U8K7og=",
      "dev": true
    },
    "bytes": {
      "version": "3.1.1",
      "resolved": "https://registry.npmjs.org/bytes/-/bytes-3.1.1.tgz",
      "integrity": "sha512-dWe4nWO/ruEOY7HkUJ5gFt1DCFV9zPRoJr8pV0/ASQermOZjtq8jMjOprC0Kd10GLN+l7xaUPvxzJFWtxGu8Fg=="
    },
    "cacache": {
      "version": "15.3.0",
      "resolved": "https://registry.npmjs.org/cacache/-/cacache-15.3.0.tgz",
      "integrity": "sha512-VVdYzXEn+cnbXpFgWs5hTT7OScegHVmLhJIR8Ufqk3iFD6A6j5iSX1KuBTfNEv4tdJWE2PzA6IVFtcLC7fN9wQ==",
      "dev": true,
      "requires": {
        "@npmcli/fs": "^1.0.0",
        "@npmcli/move-file": "^1.0.1",
        "chownr": "^2.0.0",
        "fs-minipass": "^2.0.0",
        "glob": "^7.1.4",
        "infer-owner": "^1.0.4",
        "lru-cache": "^6.0.0",
        "minipass": "^3.1.1",
        "minipass-collect": "^1.0.2",
        "minipass-flush": "^1.0.5",
        "minipass-pipeline": "^1.2.2",
        "mkdirp": "^1.0.3",
        "p-map": "^4.0.0",
        "promise-inflight": "^1.0.1",
        "rimraf": "^3.0.2",
        "ssri": "^8.0.1",
        "tar": "^6.0.2",
        "unique-filename": "^1.1.1"
      }
    },
    "cacheable-request": {
      "version": "6.1.0",
      "resolved": "https://registry.npmjs.org/cacheable-request/-/cacheable-request-6.1.0.tgz",
      "integrity": "sha512-Oj3cAGPCqOZX7Rz64Uny2GYAZNliQSqfbePrgAQ1wKAihYmCUnraBtJtKcGR4xz7wF+LoJC+ssFZvv5BgF9Igg==",
      "requires": {
        "clone-response": "^1.0.2",
        "get-stream": "^5.1.0",
        "http-cache-semantics": "^4.0.0",
        "keyv": "^3.0.0",
        "lowercase-keys": "^2.0.0",
        "normalize-url": "^4.1.0",
        "responselike": "^1.0.2"
      },
      "dependencies": {
        "get-stream": {
          "version": "5.2.0",
          "resolved": "https://registry.npmjs.org/get-stream/-/get-stream-5.2.0.tgz",
          "integrity": "sha512-nBF+F1rAZVCu/p7rjzgA+Yb4lfYXrpl7a6VmJrU8wF9I1CKvP/QwPNZHnOlwbTkY6dvtFIzFMSyQXbLoTQPRpA==",
          "requires": {
            "pump": "^3.0.0"
          }
        },
        "lowercase-keys": {
          "version": "2.0.0",
          "resolved": "https://registry.npmjs.org/lowercase-keys/-/lowercase-keys-2.0.0.tgz",
          "integrity": "sha512-tqNXrS78oMOE73NMxK4EMLQsQowWf8jKooH9g7xPavRT706R6bkQJ6DY2Te7QukaZsulxa30wQ7bk0pm4XiHmA=="
        }
      }
    },
    "call-bind": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/call-bind/-/call-bind-1.0.2.tgz",
      "integrity": "sha512-7O+FbCihrB5WGbFYesctwmTKae6rOiIzmz1icreWJ+0aA7LJfuqhEso2T9ncpcFtzMQtzXf2QGGueWJGTYsqrA==",
      "dev": true,
      "requires": {
        "function-bind": "^1.1.1",
        "get-intrinsic": "^1.0.2"
      }
    },
    "callsites": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/callsites/-/callsites-3.1.0.tgz",
      "integrity": "sha512-P8BjAsXvZS+VIDUI11hHCQEv74YT67YUi5JJFNWIqL235sBmjX4+qx9Muvls5ivyNENctx46xQLQ3aTuE7ssaQ==",
      "dev": true
    },
    "camelcase": {
      "version": "5.3.1",
      "resolved": "https://registry.npmjs.org/camelcase/-/camelcase-5.3.1.tgz",
      "integrity": "sha512-L28STB170nwWS63UjtlEOE3dldQApaJXZkOI1uMFfzf3rRuPegHaHesyee+YxQ+W6SvRDQV6UrdOdRiR153wJg==",
      "dev": true
    },
    "caniuse-lite": {
      "version": "1.0.30001303",
      "resolved": "https://registry.npmjs.org/caniuse-lite/-/caniuse-lite-1.0.30001303.tgz",
      "integrity": "sha512-/Mqc1oESndUNszJP0kx0UaQU9kEv9nNtJ7Kn8AdA0mNnH8eR1cj0kG+NbNuC1Wq/b21eA8prhKRA3bbkjONegQ==",
      "dev": true
    },
    "canonical-path": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/canonical-path/-/canonical-path-1.0.0.tgz",
      "integrity": "sha512-feylzsbDxi1gPZ1IjystzIQZagYYLvfKrSuygUCgf7z6x790VEzze5QEkdSV1U58RA7Hi0+v6fv4K54atOzATg==",
      "dev": true
    },
    "chalk": {
      "version": "2.4.2",
      "resolved": "https://registry.npmjs.org/chalk/-/chalk-2.4.2.tgz",
      "integrity": "sha512-Mti+f9lpJNcwF4tWV8/OrTTtF1gZi+f8FqlyAdouralcFWFQWF2+NgCHShjkCb+IFBLq9buZwE1xckQU4peSuQ==",
      "dev": true,
      "requires": {
        "ansi-styles": "^3.2.1",
        "escape-string-regexp": "^1.0.5",
        "supports-color": "^5.3.0"
      }
    },
    "chardet": {
      "version": "0.7.0",
      "resolved": "https://registry.npmjs.org/chardet/-/chardet-0.7.0.tgz",
      "integrity": "sha512-mT8iDcrh03qDGRRmoA2hmBJnxpllMR+0/0qlzjqZES6NdiWDcZkCNAk4rPFZ9Q85r27unkiNNg8ZOiwZXBHwcA==",
      "dev": true
    },
    "chokidar": {
      "version": "3.5.3",
      "resolved": "https://registry.npmjs.org/chokidar/-/chokidar-3.5.3.tgz",
      "integrity": "sha512-Dr3sfKRP6oTcjf2JmUmFJfeVMvXBdegxB0iVQ5eb2V10uFJUCAS8OByZdVAyVb8xXNz3GjjTgj9kLWsZTqE6kw==",
      "dev": true,
      "requires": {
        "anymatch": "~3.1.2",
        "braces": "~3.0.2",
        "fsevents": "~2.3.2",
        "glob-parent": "~5.1.2",
        "is-binary-path": "~2.1.0",
        "is-glob": "~4.0.1",
        "normalize-path": "~3.0.0",
        "readdirp": "~3.6.0"
      }
    },
    "chownr": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/chownr/-/chownr-2.0.0.tgz",
      "integrity": "sha512-bIomtDF5KGpdogkLd9VspvFzk9KfpyyGlS8YFVZl7TGPBHL5snIOnxeshwVgPteQ9b4Eydl+pVbIyE1DcvCWgQ==",
      "dev": true
    },
    "chrome-trace-event": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/chrome-trace-event/-/chrome-trace-event-1.0.3.tgz",
      "integrity": "sha512-p3KULyQg4S7NIHixdwbGX+nFHkoBiA4YQmyWtjb8XngSKV124nJmRysgAeujbUVb15vh+RvFUfCPqU7rXk+hZg==",
      "dev": true
    },
    "ci-info": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/ci-info/-/ci-info-2.0.0.tgz",
      "integrity": "sha512-5tK7EtrZ0N+OLFMthtqOj4fI2Jeb88C4CAZPu25LDVUgXJ0A3Js4PMGqrn0JU1W0Mh1/Z8wZzYPxqUrXeBboCQ=="
    },
    "circular-dependency-plugin": {
      "version": "5.2.2",
      "resolved": "https://registry.npmjs.org/circular-dependency-plugin/-/circular-dependency-plugin-5.2.2.tgz",
      "integrity": "sha512-g38K9Cm5WRwlaH6g03B9OEz/0qRizI+2I7n+Gz+L5DxXJAPAiWQvwlYNm1V1jkdpUv95bOe/ASm2vfi/G560jQ==",
      "dev": true,
      "requires": {}
    },
    "clean-stack": {
      "version": "2.2.0",
      "resolved": "https://registry.npmjs.org/clean-stack/-/clean-stack-2.2.0.tgz",
      "integrity": "sha512-4diC9HaTE+KRAMWhDhrGOECgWZxoevMc5TlkObMqNSsVU62PYzXZ/SMTjzyGAFF1YusgxGcSWTEXBhp0CPwQ1A==",
      "dev": true
    },
    "cli-boxes": {
      "version": "2.2.1",
      "resolved": "https://registry.npmjs.org/cli-boxes/-/cli-boxes-2.2.1.tgz",
      "integrity": "sha512-y4coMcylgSCdVinjiDBuR8PCC2bLjyGTwEmPb9NHR/QaNU6EUOXcTY/s6VjGMD6ENSEaeQYHCY0GNGS5jfMwPw=="
    },
    "cli-cursor": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/cli-cursor/-/cli-cursor-3.1.0.tgz",
      "integrity": "sha512-I/zHAwsKf9FqGoXM4WWRACob9+SNukZTd94DWF57E4toouRulbCxcUh6RKUEOQlYTHJnzkPMySvPNaaSLNfLZw==",
      "dev": true,
      "requires": {
        "restore-cursor": "^3.1.0"
      }
    },
    "cli-spinners": {
      "version": "2.6.1",
      "resolved": "https://registry.npmjs.org/cli-spinners/-/cli-spinners-2.6.1.tgz",
      "integrity": "sha512-x/5fWmGMnbKQAaNwN+UZlV79qBLM9JFnJuJ03gIi5whrob0xV0ofNVHy9DhwGdsMJQc2OKv0oGmLzvaqvAVv+g==",
      "dev": true
    },
    "cli-width": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/cli-width/-/cli-width-3.0.0.tgz",
      "integrity": "sha512-FxqpkPPwu1HjuN93Omfm4h8uIanXofW0RxVEW3k5RKx+mJJYSthzNhp32Kzxxy3YAEZ/Dc/EWN1vZRY0+kOhbw==",
      "dev": true
    },
    "cliui": {
      "version": "7.0.4",
      "resolved": "https://registry.npmjs.org/cliui/-/cliui-7.0.4.tgz",
      "integrity": "sha512-OcRE68cOsVMXp1Yvonl/fzkQOyjLSu/8bhPDfQt0e0/Eb283TKP20Fs2MqoPsr9SwA595rRCA+QMzYc9nBP+JQ==",
      "requires": {
        "string-width": "^4.2.0",
        "strip-ansi": "^6.0.0",
        "wrap-ansi": "^7.0.0"
      }
    },
    "clone": {
      "version": "1.0.4",
      "resolved": "https://registry.npmjs.org/clone/-/clone-1.0.4.tgz",
      "integrity": "sha1-2jCcwmPfFZlMaIypAheco8fNfH4=",
      "dev": true
    },
    "clone-deep": {
      "version": "4.0.1",
      "resolved": "https://registry.npmjs.org/clone-deep/-/clone-deep-4.0.1.tgz",
      "integrity": "sha512-neHB9xuzh/wk0dIHweyAXv2aPGZIVk3pLMe+/RNzINf17fe0OG96QroktYAUm7SM1PBnzTabaLboqqxDyMU+SQ==",
      "dev": true,
      "requires": {
        "is-plain-object": "^2.0.4",
        "kind-of": "^6.0.2",
        "shallow-clone": "^3.0.0"
      }
    },
    "clone-response": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/clone-response/-/clone-response-1.0.2.tgz",
      "integrity": "sha1-0dyXOSAxTfZ/vrlCI7TuNQI56Ws=",
      "requires": {
        "mimic-response": "^1.0.0"
      }
    },
    "color-convert": {
      "version": "1.9.3",
      "resolved": "https://registry.npmjs.org/color-convert/-/color-convert-1.9.3.tgz",
      "integrity": "sha512-QfAUtd+vFdAtFQcC8CCyYt1fYWxSqAiK2cSD6zDB8N3cpsEBAvRxp9zOGg6G/SHHJYAT88/az/IuDGALsNVbGg==",
      "dev": true,
      "requires": {
        "color-name": "1.1.3"
      }
    },
    "color-name": {
      "version": "1.1.3",
      "resolved": "https://registry.npmjs.org/color-name/-/color-name-1.1.3.tgz",
      "integrity": "sha1-p9BVi9icQveV3UIyj3QIMcpTvCU=",
      "dev": true
    },
    "color-support": {
      "version": "1.1.3",
      "resolved": "https://registry.npmjs.org/color-support/-/color-support-1.1.3.tgz",
      "integrity": "sha512-qiBjkpbMLO/HL68y+lh4q0/O1MZFj2RX6X/KmMa3+gJD3z+WwI1ZzDHysvqHGS3mP6mznPckpXmw1nI9cJjyRg==",
      "dev": true
    },
    "colorette": {
      "version": "2.0.16",
      "resolved": "https://registry.npmjs.org/colorette/-/colorette-2.0.16.tgz",
      "integrity": "sha512-hUewv7oMjCp+wkBv5Rm0v87eJhq4woh5rSR+42YSQJKecCqgIqNkZ6lAlQms/BwHPJA5NKMRlpxPRv0n8HQW6g==",
      "dev": true
    },
    "colors": {
      "version": "1.4.0",
      "resolved": "https://registry.npmjs.org/colors/-/colors-1.4.0.tgz",
      "integrity": "sha512-a+UqTh4kgZg/SlGvfbzDHpgRu7AAQOmmqRHJnxhRZICKFUT91brVhNNt58CMWU9PsBbv3PDCZUHbVxuDiH2mtA==",
      "dev": true
    },
    "commander": {
      "version": "2.20.3",
      "resolved": "https://registry.npmjs.org/commander/-/commander-2.20.3.tgz",
      "integrity": "sha512-GpVkmM8vF2vQUkj2LvZmD35JxeJOLCwJ9cUkugyk2nuhbv3+mJvpLYYt+0+USMxE+oj+ey/lJEnhZw75x/OMcQ==",
      "dev": true
    },
    "commondir": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/commondir/-/commondir-1.0.1.tgz",
      "integrity": "sha1-3dgA2gxmEnOTzKWVDqloo6rxJTs=",
      "dev": true
    },
    "component-emitter": {
      "version": "1.3.0",
      "resolved": "https://registry.npmjs.org/component-emitter/-/component-emitter-1.3.0.tgz",
      "integrity": "sha512-Rd3se6QB+sO1TwqZjscQrurpEPIfO0/yYnSin6Q/rD3mOutHvUrCAhJub3r90uNb+SESBuE0QYoB90YdfatsRg==",
      "dev": true
    },
    "compressible": {
      "version": "2.0.18",
      "resolved": "https://registry.npmjs.org/compressible/-/compressible-2.0.18.tgz",
      "integrity": "sha512-AF3r7P5dWxL8MxyITRMlORQNaOA2IkAFaTr4k7BUumjPtRpGDTZpl0Pb1XCO6JeDCBdp126Cgs9sMxqSjgYyRg==",
      "requires": {
        "mime-db": ">= 1.43.0 < 2"
      }
    },
    "compression": {
      "version": "1.7.4",
      "resolved": "https://registry.npmjs.org/compression/-/compression-1.7.4.tgz",
      "integrity": "sha512-jaSIDzP9pZVS4ZfQ+TzvtiWhdpFhE2RDHz8QJkpX9SIpLq88VueF5jJw6t+6CUQcAoA6t+x89MLrWAqpfDE8iQ==",
      "requires": {
        "accepts": "~1.3.5",
        "bytes": "3.0.0",
        "compressible": "~2.0.16",
        "debug": "2.6.9",
        "on-headers": "~1.0.2",
        "safe-buffer": "5.1.2",
        "vary": "~1.1.2"
      },
      "dependencies": {
        "bytes": {
          "version": "3.0.0",
          "resolved": "https://registry.npmjs.org/bytes/-/bytes-3.0.0.tgz",
          "integrity": "sha1-0ygVQE1olpn4Wk6k+odV3ROpYEg="
        },
        "debug": {
          "version": "2.6.9",
          "resolved": "https://registry.npmjs.org/debug/-/debug-2.6.9.tgz",
          "integrity": "sha512-bC7ElrdJaJnPbAP+1EotYvqZsb3ecl5wi6Bfi6BJTUcNowp6cvspg0jXznRTKDjm/E7AdgFBVeAPVMNcKGsHMA==",
          "requires": {
            "ms": "2.0.0"
          }
        },
        "ms": {
          "version": "2.0.0",
          "resolved": "https://registry.npmjs.org/ms/-/ms-2.0.0.tgz",
          "integrity": "sha1-VgiurfwAvmwpAd9fmGF4jeDVl8g="
        }
      }
    },
    "concat-map": {
      "version": "0.0.1",
      "resolved": "https://registry.npmjs.org/concat-map/-/concat-map-0.0.1.tgz",
      "integrity": "sha1-2Klr13/Wjfd5OnMDajug1UBdR3s=",
      "dev": true
    },
    "configstore": {
      "version": "5.0.1",
      "resolved": "https://registry.npmjs.org/configstore/-/configstore-5.0.1.tgz",
      "integrity": "sha512-aMKprgk5YhBNyH25hj8wGt2+D52Sw1DRRIzqBwLp2Ya9mFmY8KPvvtvmna8SxVR9JMZ4kzMD68N22vlaRpkeFA==",
      "requires": {
        "dot-prop": "^5.2.0",
        "graceful-fs": "^4.1.2",
        "make-dir": "^3.0.0",
        "unique-string": "^2.0.0",
        "write-file-atomic": "^3.0.0",
        "xdg-basedir": "^4.0.0"
      }
    },
    "connect": {
      "version": "3.7.0",
      "resolved": "https://registry.npmjs.org/connect/-/connect-3.7.0.tgz",
      "integrity": "sha512-ZqRXc+tZukToSNmh5C2iWMSoV3X1YUcPbqEM4DkEG5tNQXrQUZCNVGGv3IuicnkMtPfGf3Xtp8WCXs295iQ1pQ==",
      "dev": true,
      "requires": {
        "debug": "2.6.9",
        "finalhandler": "1.1.2",
        "parseurl": "~1.3.3",
        "utils-merge": "1.0.1"
      },
      "dependencies": {
        "debug": {
          "version": "2.6.9",
          "resolved": "https://registry.npmjs.org/debug/-/debug-2.6.9.tgz",
          "integrity": "sha512-bC7ElrdJaJnPbAP+1EotYvqZsb3ecl5wi6Bfi6BJTUcNowp6cvspg0jXznRTKDjm/E7AdgFBVeAPVMNcKGsHMA==",
          "dev": true,
          "requires": {
            "ms": "2.0.0"
          }
        },
        "ms": {
          "version": "2.0.0",
          "resolved": "https://registry.npmjs.org/ms/-/ms-2.0.0.tgz",
          "integrity": "sha1-VgiurfwAvmwpAd9fmGF4jeDVl8g=",
          "dev": true
        }
      }
    },
    "connect-history-api-fallback": {
      "version": "1.6.0",
      "resolved": "https://registry.npmjs.org/connect-history-api-fallback/-/connect-history-api-fallback-1.6.0.tgz",
      "integrity": "sha512-e54B99q/OUoH64zYYRf3HBP5z24G38h5D3qXu23JGRoigpX5Ss4r9ZnDk3g0Z8uQC2x2lPaJ+UlWBc1ZWBWdLg==",
      "dev": true
    },
    "connect-pause": {
      "version": "0.1.1",
      "resolved": "https://registry.npmjs.org/connect-pause/-/connect-pause-0.1.1.tgz",
      "integrity": "sha1-smmyu4Ldsaw9tQmcD7WCq6mfs3o="
    },
    "console-control-strings": {
      "version": "1.1.0",
      "resolved": "https://registry.npmjs.org/console-control-strings/-/console-control-strings-1.1.0.tgz",
      "integrity": "sha1-PXz0Rk22RG6mRL9LOVB/mFEAjo4=",
      "dev": true
    },
    "content-disposition": {
      "version": "0.5.4",
      "resolved": "https://registry.npmjs.org/content-disposition/-/content-disposition-0.5.4.tgz",
      "integrity": "sha512-FveZTNuGw04cxlAiWbzi6zTAL/lhehaWbTtgluJh4/E95DqMwTmha3KZN1aAWA8cFIhHzMZUvLevkw5Rqk+tSQ==",
      "requires": {
        "safe-buffer": "5.2.1"
      },
      "dependencies": {
        "safe-buffer": {
          "version": "5.2.1",
          "resolved": "https://registry.npmjs.org/safe-buffer/-/safe-buffer-5.2.1.tgz",
          "integrity": "sha512-rp3So07KcdmmKbGvgaNxQSJr7bGVSVk5S9Eq1F+ppbRo70+YeaDxkw5Dd8NPN+GD6bjnYm2VuPuCXmpuYvmCXQ=="
        }
      }
    },
    "content-type": {
      "version": "1.0.4",
      "resolved": "https://registry.npmjs.org/content-type/-/content-type-1.0.4.tgz",
      "integrity": "sha512-hIP3EEPs8tB9AT1L+NUqtwOAps4mk2Zob89MWXMHjHWg9milF/j4osnnQLXBCBFBk/tvIG/tUc9mOUJiPBhPXA=="
    },
    "convert-source-map": {
      "version": "1.8.0",
      "resolved": "https://registry.npmjs.org/convert-source-map/-/convert-source-map-1.8.0.tgz",
      "integrity": "sha512-+OQdjP49zViI/6i7nIJpA8rAl4sV/JdPfU9nZs3VqOwGIgizICvuN2ru6fMd+4llL0tar18UYJXfZ/TWtmhUjA==",
      "dev": true,
      "requires": {
        "safe-buffer": "~5.1.1"
      }
    },
    "cookie": {
      "version": "0.4.1",
      "resolved": "https://registry.npmjs.org/cookie/-/cookie-0.4.1.tgz",
      "integrity": "sha512-ZwrFkGJxUR3EIoXtO+yVE69Eb7KlixbaeAWfBQB9vVsNn/o+Yw69gBWSSDK825hQNdN+wF8zELf3dFNl/kxkUA=="
    },
    "cookie-signature": {
      "version": "1.0.6",
      "resolved": "https://registry.npmjs.org/cookie-signature/-/cookie-signature-1.0.6.tgz",
      "integrity": "sha1-4wOogrNCzD7oylE6eZmXNNqzriw="
    },
    "copy-anything": {
      "version": "2.0.6",
      "resolved": "https://registry.npmjs.org/copy-anything/-/copy-anything-2.0.6.tgz",
      "integrity": "sha512-1j20GZTsvKNkc4BY3NpMOM8tt///wY3FpIzozTOFO2ffuZcV61nojHXVKIy3WM+7ADCy5FVhdZYHYDdgTU0yJw==",
      "dev": true,
      "requires": {
        "is-what": "^3.14.1"
      }
    },
    "copy-webpack-plugin": {
      "version": "10.0.0",
      "resolved": "https://registry.npmjs.org/copy-webpack-plugin/-/copy-webpack-plugin-10.0.0.tgz",
      "integrity": "sha512-tuCVuFMBbRsb7IH0q1CUb50/Skv+7a6c7DJ+xi4fAbOzNLTYVMUTPnf8uGvKPtmqTvzYBrfEFo7YgP4TsUWmtg==",
      "dev": true,
      "requires": {
        "fast-glob": "^3.2.7",
        "glob-parent": "^6.0.1",
        "globby": "^12.0.2",
        "normalize-path": "^3.0.0",
        "schema-utils": "^4.0.0",
        "serialize-javascript": "^6.0.0"
      },
      "dependencies": {
        "glob-parent": {
          "version": "6.0.2",
          "resolved": "https://registry.npmjs.org/glob-parent/-/glob-parent-6.0.2.tgz",
          "integrity": "sha512-XxwI8EOhVQgWp6iDL+3b0r86f4d6AX6zSU55HfB4ydCEuXLXc5FcYeOu+nnGftS4TEju/11rt4KJPTMgbfmv4A==",
          "dev": true,
          "requires": {
            "is-glob": "^4.0.3"
          }
        },
        "schema-utils": {
          "version": "4.0.0",
          "resolved": "https://registry.npmjs.org/schema-utils/-/schema-utils-4.0.0.tgz",
          "integrity": "sha512-1edyXKgh6XnJsJSQ8mKWXnN/BVaIbFMLpouRUrXgVq7WYne5kw3MW7UPhO44uRXQSIpTSXoJbmrR2X0w9kUTyg==",
          "dev": true,
          "requires": {
            "@types/json-schema": "^7.0.9",
            "ajv": "^8.8.0",
            "ajv-formats": "^2.1.1",
            "ajv-keywords": "^5.0.0"
          }
        }
      }
    },
    "core-js": {
      "version": "3.19.3",
      "resolved": "https://registry.npmjs.org/core-js/-/core-js-3.19.3.tgz",
      "integrity": "sha512-LeLBMgEGSsG7giquSzvgBrTS7V5UL6ks3eQlUSbN8dJStlLFiRzUm5iqsRyzUB8carhfKjkJ2vzKqE6z1Vga9g==",
      "dev": true
    },
    "core-js-compat": {
      "version": "3.20.3",
      "resolved": "https://registry.npmjs.org/core-js-compat/-/core-js-compat-3.20.3.tgz",
      "integrity": "sha512-c8M5h0IkNZ+I92QhIpuSijOxGAcj3lgpsWdkCqmUTZNwidujF4r3pi6x1DCN+Vcs5qTS2XWWMfWSuCqyupX8gw==",
      "dev": true,
      "requires": {
        "browserslist": "^4.19.1",
        "semver": "7.0.0"
      },
      "dependencies": {
        "semver": {
          "version": "7.0.0",
          "resolved": "https://registry.npmjs.org/semver/-/semver-7.0.0.tgz",
          "integrity": "sha512-+GB6zVA9LWh6zovYQLALHwv5rb2PHGlJi3lfiqIHxR0uuwCgefcOJc59v9fv1w8GbStwxuuqqAjI9NMAOOgq1A==",
          "dev": true
        }
      }
    },
    "core-util-is": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/core-util-is/-/core-util-is-1.0.3.tgz",
      "integrity": "sha512-ZQBvi1DcpJ4GDqanjucZ2Hj3wEO5pZDS89BWbkcrvdxksJorwUDDZamX9ldFkp9aw2lmBDLgkObEA4DWNJ9FYQ==",
      "dev": true
    },
    "cors": {
      "version": "2.8.5",
      "resolved": "https://registry.npmjs.org/cors/-/cors-2.8.5.tgz",
      "integrity": "sha512-KIHbLJqu73RGr/hnbrO9uBeixNGuvSQjul/jdFvS/KFSIH1hWVd1ng7zOHx+YrEfInLG7q4n6GHQ9cDtxv/P6g==",
      "requires": {
        "object-assign": "^4",
        "vary": "^1"
      }
    },
    "cosmiconfig": {
      "version": "7.0.1",
      "resolved": "https://registry.npmjs.org/cosmiconfig/-/cosmiconfig-7.0.1.tgz",
      "integrity": "sha512-a1YWNUV2HwGimB7dU2s1wUMurNKjpx60HxBB6xUM8Re+2s1g1IIfJvFR0/iCF+XHdE0GMTKTuLR32UQff4TEyQ==",
      "dev": true,
      "requires": {
        "@types/parse-json": "^4.0.0",
        "import-fresh": "^3.2.1",
        "parse-json": "^5.0.0",
        "path-type": "^4.0.0",
        "yaml": "^1.10.0"
      }
    },
    "critters": {
      "version": "0.0.16",
      "resolved": "https://registry.npmjs.org/critters/-/critters-0.0.16.tgz",
      "integrity": "sha512-JwjgmO6i3y6RWtLYmXwO5jMd+maZt8Tnfu7VVISmEWyQqfLpB8soBswf8/2bu6SBXxtKA68Al3c+qIG1ApT68A==",
      "dev": true,
      "requires": {
        "chalk": "^4.1.0",
        "css-select": "^4.2.0",
        "parse5": "^6.0.1",
        "parse5-htmlparser2-tree-adapter": "^6.0.1",
        "postcss": "^8.3.7",
        "pretty-bytes": "^5.3.0"
      },
      "dependencies": {
        "ansi-styles": {
          "version": "4.3.0",
          "resolved": "https://registry.npmjs.org/ansi-styles/-/ansi-styles-4.3.0.tgz",
          "integrity": "sha512-zbB9rCJAT1rbjiVDb2hqKFHNYLxgtk8NURxZ3IZwD3F6NtxbXZQCnnSi1Lkx+IDohdPlFp222wVALIheZJQSEg==",
          "dev": true,
          "requires": {
            "color-convert": "^2.0.1"
          }
        },
        "chalk": {
          "version": "4.1.2",
          "resolved": "https://registry.npmjs.org/chalk/-/chalk-4.1.2.tgz",
          "integrity": "sha512-oKnbhFyRIXpUuez8iBMmyEa4nbj4IOQyuhc/wy9kY7/WVPcwIO9VA668Pu8RkO7+0G76SLROeyw9CpQ061i4mA==",
          "dev": true,
          "requires": {
            "ansi-styles": "^4.1.0",
            "supports-color": "^7.1.0"
          }
        },
        "color-convert": {
          "version": "2.0.1",
          "resolved": "https://registry.npmjs.org/color-convert/-/color-convert-2.0.1.tgz",
          "integrity": "sha512-RRECPsj7iu/xb5oKYcsFHSppFNnsj/52OVTRKb4zP5onXwVF3zVmmToNcOfGC+CRDpfK/U584fMg38ZHCaElKQ==",
          "dev": true,
          "requires": {
            "color-name": "~1.1.4"
          }
        },
        "color-name": {
          "version": "1.1.4",
          "resolved": "https://registry.npmjs.org/color-name/-/color-name-1.1.4.tgz",
          "integrity": "sha512-dOy+3AuW3a2wNbZHIuMZpTcgjGuLU/uBL/ubcZF9OXbDo8ff4O8yVp5Bf0efS8uEoYo5q4Fx7dY9OgQGXgAsQA==",
          "dev": true
        },
        "has-flag": {
          "version": "4.0.0",
          "resolved": "https://registry.npmjs.org/has-flag/-/has-flag-4.0.0.tgz",
          "integrity": "sha512-EykJT/Q1KjTWctppgIAgfSO0tKVuZUjhgMr17kqTumMl6Afv3EISleU7qZUzoXDFTAHTDC4NOoG/ZxU3EvlMPQ==",
          "dev": true
        },
        "supports-color": {
          "version": "7.2.0",
          "resolved": "https://registry.npmjs.org/supports-color/-/supports-color-7.2.0.tgz",
          "integrity": "sha512-qpCAvRl9stuOHveKsn7HncJRvv501qIacKzQlO/+Lwxc9+0q2wLyv4Dfvt80/DPn2pqOBsJdDiogXGR9+OvwRw==",
          "dev": true,
          "requires": {
            "has-flag": "^4.0.0"
          }
        }
      }
    },
    "cross-spawn": {
      "version": "7.0.3",
      "resolved": "https://registry.npmjs.org/cross-spawn/-/cross-spawn-7.0.3.tgz",
      "integrity": "sha512-iRDPJKUPVEND7dHPO8rkbOnPpyDygcDFtWjpeWNCgy8WP2rXcxXL8TskReQl6OrB2G7+UJrags1q15Fudc7G6w==",
      "dev": true,
      "requires": {
        "path-key": "^3.1.0",
        "shebang-command": "^2.0.0",
        "which": "^2.0.1"
      },
      "dependencies": {
        "which": {
          "version": "2.0.2",
          "resolved": "https://registry.npmjs.org/which/-/which-2.0.2.tgz",
          "integrity": "sha512-BLI3Tl1TW3Pvl70l3yq3Y64i+awpwXqsGBYWkkqMtnbXgrMD+yj7rhW0kuEDxzJaYXGjEW5ogapKNMEKNMjibA==",
          "dev": true,
          "requires": {
            "isexe": "^2.0.0"
          }
        }
      }
    },
    "crypto-random-string": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/crypto-random-string/-/crypto-random-string-2.0.0.tgz",
      "integrity": "sha512-v1plID3y9r/lPhviJ1wrXpLeyUIGAZ2SHNYTEapm7/8A9nLPoyvVp3RK/EPFqn5kEznyWgYZNsRtYYIWbuG8KA=="
    },
    "css": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/css/-/css-3.0.0.tgz",
      "integrity": "sha512-DG9pFfwOrzc+hawpmqX/dHYHJG+Bsdb0klhyi1sDneOgGOXy9wQIC8hzyVp1e4NRYDBdxcylvywPkkXCHAzTyQ==",
      "dev": true,
      "requires": {
        "inherits": "^2.0.4",
        "source-map": "^0.6.1",
        "source-map-resolve": "^0.6.0"
      },
      "dependencies": {
        "source-map": {
          "version": "0.6.1",
          "resolved": "https://registry.npmjs.org/source-map/-/source-map-0.6.1.tgz",
          "integrity": "sha512-UjgapumWlbMhkBgzT7Ykc5YXUT46F0iKu8SGXq0bcwP5dz/h0Plj6enJqjz1Zbq2l5WaqYnrVbwWOWMyF3F47g==",
          "dev": true
        }
      }
    },
    "css-blank-pseudo": {
      "version": "3.0.2",
      "resolved": "https://registry.npmjs.org/css-blank-pseudo/-/css-blank-pseudo-3.0.2.tgz",
      "integrity": "sha512-hOb1LFjRR+8ocA071xUSmg5VslJ8NGo/I2qpUpdeAYyBVCgupS5O8SEVo4SxEMYyFBNodBkzG3T1iqW9HCXxew==",
      "dev": true,
      "requires": {
        "postcss-selector-parser": "^6.0.8"
      }
    },
    "css-has-pseudo": {
      "version": "3.0.3",
      "resolved": "https://registry.npmjs.org/css-has-pseudo/-/css-has-pseudo-3.0.3.tgz",
      "integrity": "sha512-0gDYWEKaGacwxCqvQ3Ypg6wGdD1AztbMm5h1JsactG2hP2eiflj808QITmuWBpE7sjSEVrAlZhPTVd/nNMj/hQ==",
      "dev": true,
      "requires": {
        "postcss-selector-parser": "^6.0.8"
      }
    },
    "css-loader": {
      "version": "6.5.1",
      "resolved": "https://registry.npmjs.org/css-loader/-/css-loader-6.5.1.tgz",
      "integrity": "sha512-gEy2w9AnJNnD9Kuo4XAP9VflW/ujKoS9c/syO+uWMlm5igc7LysKzPXaDoR2vroROkSwsTS2tGr1yGGEbZOYZQ==",
      "dev": true,
      "requires": {
        "icss-utils": "^5.1.0",
        "postcss": "^8.2.15",
        "postcss-modules-extract-imports": "^3.0.0",
        "postcss-modules-local-by-default": "^4.0.0",
        "postcss-modules-scope": "^3.0.0",
        "postcss-modules-values": "^4.0.0",
        "postcss-value-parser": "^4.1.0",
        "semver": "^7.3.5"
      }
    },
    "css-prefers-color-scheme": {
      "version": "6.0.2",
      "resolved": "https://registry.npmjs.org/css-prefers-color-scheme/-/css-prefers-color-scheme-6.0.2.tgz",
      "integrity": "sha512-gv0KQBEM+q/XdoKyznovq3KW7ocO7k+FhPP+hQR1MenJdu0uPGS6IZa9PzlbqBeS6XcZJNAoqoFxlAUW461CrA==",
      "dev": true,
      "requires": {}
    },
    "css-select": {
      "version": "4.2.1",
      "resolved": "https://registry.npmjs.org/css-select/-/css-select-4.2.1.tgz",
      "integrity": "sha512-/aUslKhzkTNCQUB2qTX84lVmfia9NyjP3WpDGtj/WxhwBzWBYUV3DgUpurHTme8UTPcPlAD1DJ+b0nN/t50zDQ==",
      "dev": true,
      "requires": {
        "boolbase": "^1.0.0",
        "css-what": "^5.1.0",
        "domhandler": "^4.3.0",
        "domutils": "^2.8.0",
        "nth-check": "^2.0.1"
      }
    },
    "css-what": {
      "version": "5.1.0",
      "resolved": "https://registry.npmjs.org/css-what/-/css-what-5.1.0.tgz",
      "integrity": "sha512-arSMRWIIFY0hV8pIxZMEfmMI47Wj3R/aWpZDDxWYCPEiOMv6tfOrnpDtgxBYPEQD4V0Y/958+1TdC3iWTFcUPw==",
      "dev": true
    },
    "cssdb": {
      "version": "5.1.0",
      "resolved": "https://registry.npmjs.org/cssdb/-/cssdb-5.1.0.tgz",
      "integrity": "sha512-/vqjXhv1x9eGkE/zO6o8ZOI7dgdZbLVLUGyVRbPgk6YipXbW87YzUCcO+Jrmi5bwJlAH6oD+MNeZyRgXea1GZw==",
      "dev": true
    },
    "cssesc": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/cssesc/-/cssesc-3.0.0.tgz",
      "integrity": "sha512-/Tb/JcjK111nNScGob5MNtsntNM1aCNUDipB/TkwZFhyDrrE47SOx/18wF2bbjgc3ZzCSKW1T5nt5EbFoAz/Vg==",
      "dev": true
    },
    "custom-event": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/custom-event/-/custom-event-1.0.1.tgz",
      "integrity": "sha1-XQKkaFCt8bSjF5RqOSj8y1v9BCU=",
      "dev": true
    },
    "date-format": {
      "version": "4.0.3",
      "resolved": "https://registry.npmjs.org/date-format/-/date-format-4.0.3.tgz",
      "integrity": "sha512-7P3FyqDcfeznLZp2b+OMitV9Sz2lUnsT87WaTat9nVwqsBkTzPG3lPLNwW3en6F4pHUiWzr6vb8CLhjdK9bcxQ==",
      "dev": true
    },
    "debug": {
      "version": "4.3.3",
      "resolved": "https://registry.npmjs.org/debug/-/debug-4.3.3.tgz",
      "integrity": "sha512-/zxw5+vh1Tfv+4Qn7a5nsbcJKPaSvCDhojn6FEl9vupwK2VCSDtEiEtqr8DFtzYFOdz63LBkxec7DYuc2jon6Q==",
      "requires": {
        "ms": "2.1.2"
      }
    },
    "decode-uri-component": {
      "version": "0.2.0",
      "resolved": "https://registry.npmjs.org/decode-uri-component/-/decode-uri-component-0.2.0.tgz",
      "integrity": "sha1-6zkTMzRYd1y4TNGh+uBiEGu4dUU=",
      "dev": true
    },
    "decompress-response": {
      "version": "3.3.0",
      "resolved": "https://registry.npmjs.org/decompress-response/-/decompress-response-3.3.0.tgz",
      "integrity": "sha1-gKTdMjdIOEv6JICDYirt7Jgq3/M=",
      "requires": {
        "mimic-response": "^1.0.0"
      }
    },
    "deep-equal": {
      "version": "1.1.1",
      "resolved": "https://registry.npmjs.org/deep-equal/-/deep-equal-1.1.1.tgz",
      "integrity": "sha512-yd9c5AdiqVcR+JjcwUQb9DkhJc8ngNr0MahEBGvDiJw8puWab2yZlh+nkasOnZP+EGTAP6rRp2JzJhJZzvNF8g==",
      "dev": true,
      "requires": {
        "is-arguments": "^1.0.4",
        "is-date-object": "^1.0.1",
        "is-regex": "^1.0.4",
        "object-is": "^1.0.1",
        "object-keys": "^1.1.1",
        "regexp.prototype.flags": "^1.2.0"
      }
    },
    "deep-extend": {
      "version": "0.6.0",
      "resolved": "https://registry.npmjs.org/deep-extend/-/deep-extend-0.6.0.tgz",
      "integrity": "sha512-LOHxIOaPYdHlJRtCQfDIVZtfw/ufM8+rVj649RIHzcm/vGwQRXFt6OPqIFWsm2XEMrNIEtWR64sY1LEKD2vAOA=="
    },
    "default-gateway": {
      "version": "6.0.3",
      "resolved": "https://registry.npmjs.org/default-gateway/-/default-gateway-6.0.3.tgz",
      "integrity": "sha512-fwSOJsbbNzZ/CUFpqFBqYfYNLj1NbMPm8MMCIzHjC83iSJRBEGmDUxU+WP661BaBQImeC2yHwXtz+P/O9o+XEg==",
      "dev": true,
      "requires": {
        "execa": "^5.0.0"
      }
    },
    "defaults": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/defaults/-/defaults-1.0.3.tgz",
      "integrity": "sha1-xlYFHpgX2f8I7YgUd/P+QBnz730=",
      "dev": true,
      "requires": {
        "clone": "^1.0.2"
      }
    },
    "defer-to-connect": {
      "version": "1.1.3",
      "resolved": "https://registry.npmjs.org/defer-to-connect/-/defer-to-connect-1.1.3.tgz",
      "integrity": "sha512-0ISdNousHvZT2EiFlZeZAHBUvSxmKswVCEf8hW7KWgG4a8MVEu/3Vb6uWYozkjylyCxe0JBIiRB1jV45S70WVQ=="
    },
    "define-lazy-prop": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/define-lazy-prop/-/define-lazy-prop-2.0.0.tgz",
      "integrity": "sha512-Ds09qNh8yw3khSjiJjiUInaGX9xlqZDY7JVryGxdxV7NPeuqQfplOpQ66yJFZut3jLa5zOwkXw1g9EI2uKh4Og==",
      "dev": true
    },
    "define-properties": {
      "version": "1.1.3",
      "resolved": "https://registry.npmjs.org/define-properties/-/define-properties-1.1.3.tgz",
      "integrity": "sha512-3MqfYKj2lLzdMSf8ZIZE/V+Zuy+BgD6f164e8K2w7dgnpKArBDerGYpM46IYYcjnkdPNMjPk9A6VFB8+3SKlXQ==",
      "dev": true,
      "requires": {
        "object-keys": "^1.0.12"
      }
    },
    "del": {
      "version": "6.0.0",
      "resolved": "https://registry.npmjs.org/del/-/del-6.0.0.tgz",
      "integrity": "sha512-1shh9DQ23L16oXSZKB2JxpL7iMy2E0S9d517ptA1P8iw0alkPtQcrKH7ru31rYtKwF499HkTu+DRzq3TCKDFRQ==",
      "dev": true,
      "requires": {
        "globby": "^11.0.1",
        "graceful-fs": "^4.2.4",
        "is-glob": "^4.0.1",
        "is-path-cwd": "^2.2.0",
        "is-path-inside": "^3.0.2",
        "p-map": "^4.0.0",
        "rimraf": "^3.0.2",
        "slash": "^3.0.0"
      },
      "dependencies": {
        "array-union": {
          "version": "2.1.0",
          "resolved": "https://registry.npmjs.org/array-union/-/array-union-2.1.0.tgz",
          "integrity": "sha512-HGyxoOTYUyCM6stUe6EJgnd4EoewAI7zMdfqO+kGjnlZmBDz/cR5pf8r/cR4Wq60sL/p0IkcjUEEPwS3GFrIyw==",
          "dev": true
        },
        "globby": {
          "version": "11.1.0",
          "resolved": "https://registry.npmjs.org/globby/-/globby-11.1.0.tgz",
          "integrity": "sha512-jhIXaOzy1sb8IyocaruWSn1TjmnBVs8Ayhcy83rmxNJ8q2uWKCAj3CnJY+KpGSXCueAPc0i05kVvVKtP1t9S3g==",
          "dev": true,
          "requires": {
            "array-union": "^2.1.0",
            "dir-glob": "^3.0.1",
            "fast-glob": "^3.2.9",
            "ignore": "^5.2.0",
            "merge2": "^1.4.1",
            "slash": "^3.0.0"
          }
        },
        "slash": {
          "version": "3.0.0",
          "resolved": "https://registry.npmjs.org/slash/-/slash-3.0.0.tgz",
          "integrity": "sha512-g9Q1haeby36OSStwb4ntCGGGaKsaVSjQ68fBxoQcutl5fS1vuY18H3wSt3jFyFtrkx+Kz0V1G85A4MyAdDMi2Q==",
          "dev": true
        }
      }
    },
    "delegates": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/delegates/-/delegates-1.0.0.tgz",
      "integrity": "sha1-hMbhWbgZBP3KWaDvRM2HDTElD5o=",
      "dev": true
    },
    "depd": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/depd/-/depd-1.1.2.tgz",
      "integrity": "sha1-m81S4UwJd2PnSbJ0xDRu0uVgtak="
    },
    "dependency-graph": {
      "version": "0.11.0",
      "resolved": "https://registry.npmjs.org/dependency-graph/-/dependency-graph-0.11.0.tgz",
      "integrity": "sha512-JeMq7fEshyepOWDfcfHK06N3MhyPhz++vtqWhMT5O9A3K42rdsEDpfdVqjaqaAhsw6a+ZqeDvQVtD0hFHQWrzg==",
      "dev": true
    },
    "destroy": {
      "version": "1.0.4",
      "resolved": "https://registry.npmjs.org/destroy/-/destroy-1.0.4.tgz",
      "integrity": "sha1-l4hXRCxEdJ5CBmE+N5RiBYJqvYA="
    },
    "detect-node": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/detect-node/-/detect-node-2.1.0.tgz",
      "integrity": "sha512-T0NIuQpnTvFDATNuHN5roPwSBG83rFsuO+MXXH9/3N1eFbn4wcPjttvjMLEPWJ0RGUYgQE7cGgS3tNxbqCGM7g==",
      "dev": true
    },
    "di": {
      "version": "0.0.1",
      "resolved": "https://registry.npmjs.org/di/-/di-0.0.1.tgz",
      "integrity": "sha1-gGZJMmzqp8qjMG112YXqJ0i6kTw=",
      "dev": true
    },
    "dir-glob": {
      "version": "3.0.1",
      "resolved": "https://registry.npmjs.org/dir-glob/-/dir-glob-3.0.1.tgz",
      "integrity": "sha512-WkrWp9GR4KXfKGYzOLmTuGVi1UWFfws377n9cc55/tb6DuqyF6pcQ5AbiHEshaDpY9v6oaSr2XCDidGmMwdzIA==",
      "dev": true,
      "requires": {
        "path-type": "^4.0.0"
      }
    },
    "dns-equal": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/dns-equal/-/dns-equal-1.0.0.tgz",
      "integrity": "sha1-s55/HabrCnW6nBcySzR1PEfgZU0=",
      "dev": true
    },
    "dns-packet": {
      "version": "1.3.4",
      "resolved": "https://registry.npmjs.org/dns-packet/-/dns-packet-1.3.4.tgz",
      "integrity": "sha512-BQ6F4vycLXBvdrJZ6S3gZewt6rcrks9KBgM9vrhW+knGRqc8uEdT7fuCwloc7nny5xNoMJ17HGH0R/6fpo8ECA==",
      "dev": true,
      "requires": {
        "ip": "^1.1.0",
        "safe-buffer": "^5.0.1"
      }
    },
    "dns-txt": {
      "version": "2.0.2",
      "resolved": "https://registry.npmjs.org/dns-txt/-/dns-txt-2.0.2.tgz",
      "integrity": "sha1-uR2Ab10nGI5Ks+fRB9iBocxGQrY=",
      "dev": true,
      "requires": {
        "buffer-indexof": "^1.0.0"
      }
    },
    "dom-serialize": {
      "version": "2.2.1",
      "resolved": "https://registry.npmjs.org/dom-serialize/-/dom-serialize-2.2.1.tgz",
      "integrity": "sha1-ViromZ9Evl6jB29UGdzVnrQ6yVs=",
      "dev": true,
      "requires": {
        "custom-event": "~1.0.0",
        "ent": "~2.2.0",
        "extend": "^3.0.0",
        "void-elements": "^2.0.0"
      }
    },
    "dom-serializer": {
      "version": "1.3.2",
      "resolved": "https://registry.npmjs.org/dom-serializer/-/dom-serializer-1.3.2.tgz",
      "integrity": "sha512-5c54Bk5Dw4qAxNOI1pFEizPSjVsx5+bpJKmL2kPn8JhBUq2q09tTCa3mjijun2NfK78NMouDYNMBkOrPZiS+ig==",
      "dev": true,
      "requires": {
        "domelementtype": "^2.0.1",
        "domhandler": "^4.2.0",
        "entities": "^2.0.0"
      }
    },
    "domelementtype": {
      "version": "2.2.0",
      "resolved": "https://registry.npmjs.org/domelementtype/-/domelementtype-2.2.0.tgz",
      "integrity": "sha512-DtBMo82pv1dFtUmHyr48beiuq792Sxohr+8Hm9zoxklYPfa6n0Z3Byjj2IV7bmr2IyqClnqEQhfgHJJ5QF0R5A==",
      "dev": true
    },
    "domhandler": {
      "version": "4.3.0",
      "resolved": "https://registry.npmjs.org/domhandler/-/domhandler-4.3.0.tgz",
      "integrity": "sha512-fC0aXNQXqKSFTr2wDNZDhsEYjCiYsDWl3D01kwt25hm1YIPyDGHvvi3rw+PLqHAl/m71MaiF7d5zvBr0p5UB2g==",
      "dev": true,
      "requires": {
        "domelementtype": "^2.2.0"
      }
    },
    "domutils": {
      "version": "2.8.0",
      "resolved": "https://registry.npmjs.org/domutils/-/domutils-2.8.0.tgz",
      "integrity": "sha512-w96Cjofp72M5IIhpjgobBimYEfoPjx1Vx0BSX9P30WBdZW2WIKU0T1Bd0kz2eNZ9ikjKgHbEyKx8BB6H1L3h3A==",
      "dev": true,
      "requires": {
        "dom-serializer": "^1.0.1",
        "domelementtype": "^2.2.0",
        "domhandler": "^4.2.0"
      }
    },
    "dot-prop": {
      "version": "5.3.0",
      "resolved": "https://registry.npmjs.org/dot-prop/-/dot-prop-5.3.0.tgz",
      "integrity": "sha512-QM8q3zDe58hqUqjraQOmzZ1LIH9SWQJTlEKCH4kJ2oQvLZk7RbQXvtDM2XEq3fwkV9CCvvH4LA0AV+ogFsBM2Q==",
      "requires": {
        "is-obj": "^2.0.0"
      }
    },
    "duplexer3": {
      "version": "0.1.4",
      "resolved": "https://registry.npmjs.org/duplexer3/-/duplexer3-0.1.4.tgz",
      "integrity": "sha1-7gHdHKwO08vH/b6jfcCo8c4ALOI="
    },
    "ee-first": {
      "version": "1.1.1",
      "resolved": "https://registry.npmjs.org/ee-first/-/ee-first-1.1.1.tgz",
      "integrity": "sha1-WQxhFWsK4vTwJVcyoViyZrxWsh0="
    },
    "electron-to-chromium": {
      "version": "1.4.56",
      "resolved": "https://registry.npmjs.org/electron-to-chromium/-/electron-to-chromium-1.4.56.tgz",
      "integrity": "sha512-0k/S0FQqRRpJbX7YUjwCcLZ8D42RqGKtaiq90adXBOYgTIWwLA/g3toO8k9yEpqU8iC4QyaWYYWSTBIna8WV4g==",
      "dev": true
    },
    "emoji-regex": {
      "version": "8.0.0",
      "resolved": "https://registry.npmjs.org/emoji-regex/-/emoji-regex-8.0.0.tgz",
      "integrity": "sha512-MSjYzcWNOA0ewAHpz0MxpYFvwg6yjy1NG3xteoqz644VCo/RPgnr1/GGt+ic3iJTzQ8Eu3TdM14SawnVUmGE6A=="
    },
    "emojis-list": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/emojis-list/-/emojis-list-3.0.0.tgz",
      "integrity": "sha512-/kyM18EfinwXZbno9FyUGeFh87KC8HRQBQGildHZbEuRyWFOmv1U10o9BBp8XVZDVNNuQKyIGIu5ZYAAXJ0V2Q==",
      "dev": true
    },
    "encodeurl": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/encodeurl/-/encodeurl-1.0.2.tgz",
      "integrity": "sha1-rT/0yG7C0CkyL1oCw6mmBslbP1k="
    },
    "encoding": {
      "version": "0.1.13",
      "resolved": "https://registry.npmjs.org/encoding/-/encoding-0.1.13.tgz",
      "integrity": "sha512-ETBauow1T35Y/WZMkio9jiM0Z5xjHHmJ4XmjZOq1l/dXz3lr2sRn87nJy20RupqSh1F2m3HHPSp8ShIPQJrJ3A==",
      "dev": true,
      "optional": true,
      "requires": {
        "iconv-lite": "^0.6.2"
      },
      "dependencies": {
        "iconv-lite": {
          "version": "0.6.3",
          "resolved": "https://registry.npmjs.org/iconv-lite/-/iconv-lite-0.6.3.tgz",
          "integrity": "sha512-4fCk79wshMdzMp2rH06qWrJE4iolqLhCUH+OiuIgU++RB0+94NlDL81atO7GX55uUKueo0txHNtvEyI6D7WdMw==",
          "dev": true,
          "optional": true,
          "requires": {
            "safer-buffer": ">= 2.1.2 < 3.0.0"
          }
        }
      }
    },
    "end-of-stream": {
      "version": "1.4.4",
      "resolved": "https://registry.npmjs.org/end-of-stream/-/end-of-stream-1.4.4.tgz",
      "integrity": "sha512-+uw1inIHVPQoaVuHzRyXd21icM+cnt4CzD5rW+NC1wjOUSTOs+Te7FOv7AhN7vS9x/oIyhLP5PR1H+phQAHu5Q==",
      "requires": {
        "once": "^1.4.0"
      }
    },
    "engine.io": {
      "version": "6.1.2",
      "resolved": "https://registry.npmjs.org/engine.io/-/engine.io-6.1.2.tgz",
      "integrity": "sha512-v/7eGHxPvO2AWsksyx2PUsQvBafuvqs0jJJQ0FdmJG1b9qIvgSbqDRGwNhfk2XHaTTbTXiC4quRE8Q9nRjsrQQ==",
      "dev": true,
      "requires": {
        "@types/cookie": "^0.4.1",
        "@types/cors": "^2.8.12",
        "@types/node": ">=10.0.0",
        "accepts": "~1.3.4",
        "base64id": "2.0.0",
        "cookie": "~0.4.1",
        "cors": "~2.8.5",
        "debug": "~4.3.1",
        "engine.io-parser": "~5.0.0",
        "ws": "~8.2.3"
      }
    },
    "engine.io-parser": {
      "version": "5.0.3",
      "resolved": "https://registry.npmjs.org/engine.io-parser/-/engine.io-parser-5.0.3.tgz",
      "integrity": "sha512-BtQxwF27XUNnSafQLvDi0dQ8s3i6VgzSoQMJacpIcGNrlUdfHSKbgm3jmjCVvQluGzqwujQMPAoMai3oYSTurg==",
      "dev": true,
      "requires": {
        "@socket.io/base64-arraybuffer": "~1.0.2"
      }
    },
    "enhanced-resolve": {
      "version": "5.8.3",
      "resolved": "https://registry.npmjs.org/enhanced-resolve/-/enhanced-resolve-5.8.3.tgz",
      "integrity": "sha512-EGAbGvH7j7Xt2nc0E7D99La1OiEs8LnyimkRgwExpUMScN6O+3x9tIWs7PLQZVNx4YD+00skHXPXi1yQHpAmZA==",
      "dev": true,
      "requires": {
        "graceful-fs": "^4.2.4",
        "tapable": "^2.2.0"
      }
    },
    "ent": {
      "version": "2.2.0",
      "resolved": "https://registry.npmjs.org/ent/-/ent-2.2.0.tgz",
      "integrity": "sha1-6WQhkyWiHQX0RGai9obtbOX13R0=",
      "dev": true
    },
    "entities": {
      "version": "2.2.0",
      "resolved": "https://registry.npmjs.org/entities/-/entities-2.2.0.tgz",
      "integrity": "sha512-p92if5Nz619I0w+akJrLZH0MX0Pb5DX39XOwQTtXSdQQOaYH03S1uIQp4mhOZtAXrxq4ViO67YTiLBo2638o9A==",
      "dev": true
    },
    "env-paths": {
      "version": "2.2.1",
      "resolved": "https://registry.npmjs.org/env-paths/-/env-paths-2.2.1.tgz",
      "integrity": "sha512-+h1lkLKhZMTYjog1VEpJNG7NZJWcuc2DDk/qsqSTRRCOXiLjeQ1d1/udrUGhqMxUgAlwKNZ0cf2uqan5GLuS2A==",
      "dev": true
    },
    "err-code": {
      "version": "2.0.3",
      "resolved": "https://registry.npmjs.org/err-code/-/err-code-2.0.3.tgz",
      "integrity": "sha512-2bmlRpNKBxT/CRmPOlyISQpNj+qSeYvcym/uT0Jx2bMOlKLtSy1ZmLuVxSEKKyor/N5yhvp/ZiG1oE3DEYMSFA==",
      "dev": true
    },
    "errno": {
      "version": "0.1.8",
      "resolved": "https://registry.npmjs.org/errno/-/errno-0.1.8.tgz",
      "integrity": "sha512-dJ6oBr5SQ1VSd9qkk7ByRgb/1SH4JZjCHSW/mr63/QcXO9zLVxvJ6Oy13nio03rxpSnVDDjFor75SjVeZWPW/A==",
      "dev": true,
      "optional": true,
      "requires": {
        "prr": "~1.0.1"
      }
    },
    "error-ex": {
      "version": "1.3.2",
      "resolved": "https://registry.npmjs.org/error-ex/-/error-ex-1.3.2.tgz",
      "integrity": "sha512-7dFHNmqeFSEt2ZBsCriorKnn3Z2pj+fd9kmI6QoWw4//DL+icEBfc0U7qJCisqrTsKTjw4fNFy2pW9OqStD84g==",
      "dev": true,
      "requires": {
        "is-arrayish": "^0.2.1"
      }
    },
    "errorhandler": {
      "version": "1.5.1",
      "resolved": "https://registry.npmjs.org/errorhandler/-/errorhandler-1.5.1.tgz",
      "integrity": "sha512-rcOwbfvP1WTViVoUjcfZicVzjhjTuhSMntHh6mW3IrEiyE6mJyXvsToJUJGlGlw/2xU9P5whlWNGlIDVeCiT4A==",
      "requires": {
        "accepts": "~1.3.7",
        "escape-html": "~1.0.3"
      }
    },
    "es-module-lexer": {
      "version": "0.9.3",
      "resolved": "https://registry.npmjs.org/es-module-lexer/-/es-module-lexer-0.9.3.tgz",
      "integrity": "sha512-1HQ2M2sPtxwnvOvT1ZClHyQDiggdNjURWpY2we6aMKCQiUVxTmVs2UYPLIrD84sS+kMdUwfBSylbJPwNnBrnHQ==",
      "dev": true
    },
    "esbuild": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild/-/esbuild-0.14.11.tgz",
      "integrity": "sha512-xZvPtVj6yecnDeFb3KjjCM6i7B5TCAQZT77kkW/CpXTMnd6VLnRPKrUB1XHI1pSq6a4Zcy3BGueQ8VljqjDGCg==",
      "dev": true,
      "optional": true,
      "requires": {
        "esbuild-android-arm64": "0.14.11",
        "esbuild-darwin-64": "0.14.11",
        "esbuild-darwin-arm64": "0.14.11",
        "esbuild-freebsd-64": "0.14.11",
        "esbuild-freebsd-arm64": "0.14.11",
        "esbuild-linux-32": "0.14.11",
        "esbuild-linux-64": "0.14.11",
        "esbuild-linux-arm": "0.14.11",
        "esbuild-linux-arm64": "0.14.11",
        "esbuild-linux-mips64le": "0.14.11",
        "esbuild-linux-ppc64le": "0.14.11",
        "esbuild-linux-s390x": "0.14.11",
        "esbuild-netbsd-64": "0.14.11",
        "esbuild-openbsd-64": "0.14.11",
        "esbuild-sunos-64": "0.14.11",
        "esbuild-windows-32": "0.14.11",
        "esbuild-windows-64": "0.14.11",
        "esbuild-windows-arm64": "0.14.11"
      }
    },
    "esbuild-android-arm64": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-android-arm64/-/esbuild-android-arm64-0.14.11.tgz",
      "integrity": "sha512-6iHjgvMnC/SzDH8TefL+/3lgCjYWwAd1LixYfmz/TBPbDQlxcuSkX0yiQgcJB9k+ibZ54yjVXziIwGdlc+6WNw==",
      "dev": true,
      "optional": true
    },
    "esbuild-darwin-64": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-darwin-64/-/esbuild-darwin-64-0.14.11.tgz",
      "integrity": "sha512-olq84ikh6TiBcrs3FnM4eR5VPPlcJcdW8BnUz/lNoEWYifYQ+Po5DuYV1oz1CTFMw4k6bQIZl8T3yxL+ZT2uvQ==",
      "dev": true,
      "optional": true
    },
    "esbuild-darwin-arm64": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-darwin-arm64/-/esbuild-darwin-arm64-0.14.11.tgz",
      "integrity": "sha512-Jj0ieWLREPBYr/TZJrb2GFH8PVzDqiQWavo1pOFFShrcmHWDBDrlDxPzEZ67NF/Un3t6sNNmeI1TUS/fe1xARg==",
      "dev": true,
      "optional": true
    },
    "esbuild-freebsd-64": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-freebsd-64/-/esbuild-freebsd-64-0.14.11.tgz",
      "integrity": "sha512-C5sT3/XIztxxz/zwDjPRHyzj/NJFOnakAanXuyfLDwhwupKPd76/PPHHyJx6Po6NI6PomgVp/zi6GRB8PfrOTA==",
      "dev": true,
      "optional": true
    },
    "esbuild-freebsd-arm64": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-freebsd-arm64/-/esbuild-freebsd-arm64-0.14.11.tgz",
      "integrity": "sha512-y3Llu4wbs0bk4cwjsdAtVOesXb6JkdfZDLKMt+v1U3tOEPBdSu6w8796VTksJgPfqvpX22JmPLClls0h5p+L9w==",
      "dev": true,
      "optional": true
    },
    "esbuild-linux-32": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-linux-32/-/esbuild-linux-32-0.14.11.tgz",
      "integrity": "sha512-Cg3nVsxArjyLke9EuwictFF3Sva+UlDTwHIuIyx8qpxRYAOUTmxr2LzYrhHyTcGOleLGXUXYsnUVwKqnKAgkcg==",
      "dev": true,
      "optional": true
    },
    "esbuild-linux-64": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-linux-64/-/esbuild-linux-64-0.14.11.tgz",
      "integrity": "sha512-oeR6dIrrojr8DKVrxtH3xl4eencmjsgI6kPkDCRIIFwv4p+K7ySviM85K66BN01oLjzthpUMvBVfWSJkBLeRbg==",
      "dev": true,
      "optional": true
    },
    "esbuild-linux-arm": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-linux-arm/-/esbuild-linux-arm-0.14.11.tgz",
      "integrity": "sha512-vcwskfD9g0tojux/ZaTJptJQU3a7YgTYsptK1y6LQ/rJmw7U5QJvboNawqM98Ca3ToYEucfCRGbl66OTNtp6KQ==",
      "dev": true,
      "optional": true
    },
    "esbuild-linux-arm64": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-linux-arm64/-/esbuild-linux-arm64-0.14.11.tgz",
      "integrity": "sha512-+e6ZCgTFQYZlmg2OqLkg1jHLYtkNDksxWDBWNtI4XG4WxuOCUErLqfEt9qWjvzK3XBcCzHImrajkUjO+rRkbMg==",
      "dev": true,
      "optional": true
    },
    "esbuild-linux-mips64le": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-linux-mips64le/-/esbuild-linux-mips64le-0.14.11.tgz",
      "integrity": "sha512-Rrs99L+p54vepmXIb87xTG6ukrQv+CzrM8eoeR+r/OFL2Rg8RlyEtCeshXJ2+Q66MXZOgPJaokXJZb9snq28bw==",
      "dev": true,
      "optional": true
    },
    "esbuild-linux-ppc64le": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-linux-ppc64le/-/esbuild-linux-ppc64le-0.14.11.tgz",
      "integrity": "sha512-JyzziGAI0D30Vyzt0HDihp4s1IUtJ3ssV2zx9O/c+U/dhUHVP2TmlYjzCfCr2Q6mwXTeloDcLS4qkyvJtYptdQ==",
      "dev": true,
      "optional": true
    },
    "esbuild-linux-s390x": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-linux-s390x/-/esbuild-linux-s390x-0.14.11.tgz",
      "integrity": "sha512-DoThrkzunZ1nfRGoDN6REwmo8ZZWHd2ztniPVIR5RMw/Il9wiWEYBahb8jnMzQaSOxBsGp0PbyJeVLTUatnlcw==",
      "dev": true,
      "optional": true
    },
    "esbuild-netbsd-64": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-netbsd-64/-/esbuild-netbsd-64-0.14.11.tgz",
      "integrity": "sha512-12luoRQz+6eihKYh1zjrw0CBa2aw3twIiHV/FAfjh2NEBDgJQOY4WCEUEN+Rgon7xmLh4XUxCQjnwrvf8zhACw==",
      "dev": true,
      "optional": true
    },
    "esbuild-openbsd-64": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-openbsd-64/-/esbuild-openbsd-64-0.14.11.tgz",
      "integrity": "sha512-l18TZDjmvwW6cDeR4fmizNoxndyDHamGOOAenwI4SOJbzlJmwfr0jUgjbaXCUuYVOA964siw+Ix+A+bhALWg8Q==",
      "dev": true,
      "optional": true
    },
    "esbuild-sunos-64": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-sunos-64/-/esbuild-sunos-64-0.14.11.tgz",
      "integrity": "sha512-bmYzDtwASBB8c+0/HVOAiE9diR7+8zLm/i3kEojUH2z0aIs6x/S4KiTuT5/0VKJ4zk69kXel1cNWlHBMkmavQg==",
      "dev": true,
      "optional": true
    },
    "esbuild-wasm": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-wasm/-/esbuild-wasm-0.14.11.tgz",
      "integrity": "sha512-9e1R6hv0hiU+BkJI2edqUuWfXUbOP2Mox+Ijl/uY1vLLlSsunkrcADqD/4Rz+VCEDzw6ecscJM+uJqR2fRmEUg==",
      "dev": true
    },
    "esbuild-windows-32": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-windows-32/-/esbuild-windows-32-0.14.11.tgz",
      "integrity": "sha512-J1Ys5hMid8QgdY00OBvIolXgCQn1ARhYtxPnG6ESWNTty3ashtc4+As5nTrsErnv8ZGUcWZe4WzTP/DmEVX1UQ==",
      "dev": true,
      "optional": true
    },
    "esbuild-windows-64": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-windows-64/-/esbuild-windows-64-0.14.11.tgz",
      "integrity": "sha512-h9FmMskMuGeN/9G9+LlHPAoiQk9jlKDUn9yA0MpiGzwLa82E7r1b1u+h2a+InprbSnSLxDq/7p5YGtYVO85Mlg==",
      "dev": true,
      "optional": true
    },
    "esbuild-windows-arm64": {
      "version": "0.14.11",
      "resolved": "https://registry.npmjs.org/esbuild-windows-arm64/-/esbuild-windows-arm64-0.14.11.tgz",
      "integrity": "sha512-dZp7Krv13KpwKklt9/1vBFBMqxEQIO6ri7Azf8C+ob4zOegpJmha2XY9VVWP/OyQ0OWk6cEeIzMJwInRZrzBUQ==",
      "dev": true,
      "optional": true
    },
    "escalade": {
      "version": "3.1.1",
      "resolved": "https://registry.npmjs.org/escalade/-/escalade-3.1.1.tgz",
      "integrity": "sha512-k0er2gUkLf8O0zKJiAhmkTnJlTvINGv7ygDNPbeIsX/TJjGJZHuh9B2UxbsaEkmlEo9MfhrSzmhIlhRlI2GXnw=="
    },
    "escape-goat": {
      "version": "2.1.1",
      "resolved": "https://registry.npmjs.org/escape-goat/-/escape-goat-2.1.1.tgz",
      "integrity": "sha512-8/uIhbG12Csjy2JEW7D9pHbreaVaS/OpN3ycnyvElTdwM5n6GY6W6e2IPemfvGZeUMqZ9A/3GqIZMgKnBhAw/Q=="
    },
    "escape-html": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/escape-html/-/escape-html-1.0.3.tgz",
      "integrity": "sha1-Aljq5NPQwJdN4cFpGI7wBR0dGYg="
    },
    "escape-string-regexp": {
      "version": "1.0.5",
      "resolved": "https://registry.npmjs.org/escape-string-regexp/-/escape-string-regexp-1.0.5.tgz",
      "integrity": "sha1-G2HAViGQqN/2rjuyzwIAyhMLhtQ=",
      "dev": true
    },
    "eslint-scope": {
      "version": "5.1.1",
      "resolved": "https://registry.npmjs.org/eslint-scope/-/eslint-scope-5.1.1.tgz",
      "integrity": "sha512-2NxwbF/hZ0KpepYN0cNbo+FN6XoK7GaHlQhgx/hIZl6Va0bF45RQOOwhLIy8lQDbuCiadSLCBnH2CFYquit5bw==",
      "dev": true,
      "requires": {
        "esrecurse": "^4.3.0",
        "estraverse": "^4.1.1"
      }
    },
    "esprima": {
      "version": "4.0.1",
      "resolved": "https://registry.npmjs.org/esprima/-/esprima-4.0.1.tgz",
      "integrity": "sha512-eGuFFw7Upda+g4p+QHvnW0RyTX/SVeJBDM/gCtMARO0cLuT2HcEKnTPvhjV6aGeqrCB/sbNop0Kszm0jsaWU4A==",
      "dev": true
    },
    "esrecurse": {
      "version": "4.3.0",
      "resolved": "https://registry.npmjs.org/esrecurse/-/esrecurse-4.3.0.tgz",
      "integrity": "sha512-KmfKL3b6G+RXvP8N1vr3Tq1kL/oCFgn2NYXEtqP8/L3pKapUA4G8cFVaoF3SU323CD4XypR/ffioHmkti6/Tag==",
      "dev": true,
      "requires": {
        "estraverse": "^5.2.0"
      },
      "dependencies": {
        "estraverse": {
          "version": "5.3.0",
          "resolved": "https://registry.npmjs.org/estraverse/-/estraverse-5.3.0.tgz",
          "integrity": "sha512-MMdARuVEQziNTeJD8DgMqmhwR11BRQ/cBP+pLtYdSTnf3MIO8fFeiINEbX36ZdNlfU/7A9f3gUw49B3oQsvwBA==",
          "dev": true
        }
      }
    },
    "estraverse": {
      "version": "4.3.0",
      "resolved": "https://registry.npmjs.org/estraverse/-/estraverse-4.3.0.tgz",
      "integrity": "sha512-39nnKffWz8xN1BU/2c79n9nB9HDzo0niYUqx6xyqUnyoAnQyyWpOTdZEeiCch8BBu515t4wp9ZmgVfVhn9EBpw==",
      "dev": true
    },
    "esutils": {
      "version": "2.0.3",
      "resolved": "https://registry.npmjs.org/esutils/-/esutils-2.0.3.tgz",
      "integrity": "sha512-kVscqXk4OCp68SZ0dkgEKVi6/8ij300KBWTJq32P/dYeWTSwK41WyTxalN1eRmA5Z9UU/LX9D7FWSmV9SAYx6g==",
      "dev": true
    },
    "etag": {
      "version": "1.8.1",
      "resolved": "https://registry.npmjs.org/etag/-/etag-1.8.1.tgz",
      "integrity": "sha1-Qa4u62XvpiJorr/qg6x9eSmbCIc="
    },
    "eventemitter-asyncresource": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/eventemitter-asyncresource/-/eventemitter-asyncresource-1.0.0.tgz",
      "integrity": "sha512-39F7TBIV0G7gTelxwbEqnwhp90eqCPON1k0NwNfwhgKn4Co4ybUbj2pECcXT0B3ztRKZ7Pw1JujUUgmQJHcVAQ==",
      "dev": true
    },
    "eventemitter3": {
      "version": "4.0.7",
      "resolved": "https://registry.npmjs.org/eventemitter3/-/eventemitter3-4.0.7.tgz",
      "integrity": "sha512-8guHBZCwKnFhYdHr2ysuRWErTwhoN2X8XELRlrRwpmfeY2jjuUN4taQMsULKUVo1K4DvZl+0pgfyoysHxvmvEw==",
      "dev": true
    },
    "events": {
      "version": "3.3.0",
      "resolved": "https://registry.npmjs.org/events/-/events-3.3.0.tgz",
      "integrity": "sha512-mQw+2fkQbALzQ7V0MY0IqdnXNOeTtP4r0lN9z7AAawCXgqea7bDii20AYrIBrFd/Hx0M2Ocz6S111CaFkUcb0Q==",
      "dev": true
    },
    "execa": {
      "version": "5.1.1",
      "resolved": "https://registry.npmjs.org/execa/-/execa-5.1.1.tgz",
      "integrity": "sha512-8uSpZZocAZRBAPIEINJj3Lo9HyGitllczc27Eh5YYojjMFMn8yHMDMaUHE2Jqfq05D/wucwI4JGURyXt1vchyg==",
      "dev": true,
      "requires": {
        "cross-spawn": "^7.0.3",
        "get-stream": "^6.0.0",
        "human-signals": "^2.1.0",
        "is-stream": "^2.0.0",
        "merge-stream": "^2.0.0",
        "npm-run-path": "^4.0.1",
        "onetime": "^5.1.2",
        "signal-exit": "^3.0.3",
        "strip-final-newline": "^2.0.0"
      }
    },
    "express": {
      "version": "4.17.2",
      "resolved": "https://registry.npmjs.org/express/-/express-4.17.2.tgz",
      "integrity": "sha512-oxlxJxcQlYwqPWKVJJtvQiwHgosH/LrLSPA+H4UxpyvSS6jC5aH+5MoHFM+KABgTOt0APue4w66Ha8jCUo9QGg==",
      "requires": {
        "accepts": "~1.3.7",
        "array-flatten": "1.1.1",
        "body-parser": "1.19.1",
        "content-disposition": "0.5.4",
        "content-type": "~1.0.4",
        "cookie": "0.4.1",
        "cookie-signature": "1.0.6",
        "debug": "2.6.9",
        "depd": "~1.1.2",
        "encodeurl": "~1.0.2",
        "escape-html": "~1.0.3",
        "etag": "~1.8.1",
        "finalhandler": "~1.1.2",
        "fresh": "0.5.2",
        "merge-descriptors": "1.0.1",
        "methods": "~1.1.2",
        "on-finished": "~2.3.0",
        "parseurl": "~1.3.3",
        "path-to-regexp": "0.1.7",
        "proxy-addr": "~2.0.7",
        "qs": "6.9.6",
        "range-parser": "~1.2.1",
        "safe-buffer": "5.2.1",
        "send": "0.17.2",
        "serve-static": "1.14.2",
        "setprototypeof": "1.2.0",
        "statuses": "~1.5.0",
        "type-is": "~1.6.18",
        "utils-merge": "1.0.1",
        "vary": "~1.1.2"
      },
      "dependencies": {
        "array-flatten": {
          "version": "1.1.1",
          "resolved": "https://registry.npmjs.org/array-flatten/-/array-flatten-1.1.1.tgz",
          "integrity": "sha1-ml9pkFGx5wczKPKgCJaLZOopVdI="
        },
        "debug": {
          "version": "2.6.9",
          "resolved": "https://registry.npmjs.org/debug/-/debug-2.6.9.tgz",
          "integrity": "sha512-bC7ElrdJaJnPbAP+1EotYvqZsb3ecl5wi6Bfi6BJTUcNowp6cvspg0jXznRTKDjm/E7AdgFBVeAPVMNcKGsHMA==",
          "requires": {
            "ms": "2.0.0"
          }
        },
        "ms": {
          "version": "2.0.0",
          "resolved": "https://registry.npmjs.org/ms/-/ms-2.0.0.tgz",
          "integrity": "sha1-VgiurfwAvmwpAd9fmGF4jeDVl8g="
        },
        "safe-buffer": {
          "version": "5.2.1",
          "resolved": "https://registry.npmjs.org/safe-buffer/-/safe-buffer-5.2.1.tgz",
          "integrity": "sha512-rp3So07KcdmmKbGvgaNxQSJr7bGVSVk5S9Eq1F+ppbRo70+YeaDxkw5Dd8NPN+GD6bjnYm2VuPuCXmpuYvmCXQ=="
        }
      }
    },
    "express-urlrewrite": {
      "version": "1.4.0",
      "resolved": "https://registry.npmjs.org/express-urlrewrite/-/express-urlrewrite-1.4.0.tgz",
      "integrity": "sha512-PI5h8JuzoweS26vFizwQl6UTF25CAHSggNv0J25Dn/IKZscJHWZzPrI5z2Y2jgOzIaw2qh8l6+/jUcig23Z2SA==",
      "requires": {
        "debug": "*",
        "path-to-regexp": "^1.0.3"
      },
      "dependencies": {
        "isarray": {
          "version": "0.0.1",
          "resolved": "https://registry.npmjs.org/isarray/-/isarray-0.0.1.tgz",
          "integrity": "sha1-ihis/Kmo9Bd+Cav8YDiTmwXR7t8="
        },
        "path-to-regexp": {
          "version": "1.8.0",
          "resolved": "https://registry.npmjs.org/path-to-regexp/-/path-to-regexp-1.8.0.tgz",
          "integrity": "sha512-n43JRhlUKUAlibEJhPeir1ncUID16QnEjNpwzNdO3Lm4ywrBpBZ5oLD0I6br9evr1Y9JTqwRtAh7JLoOzAQdVA==",
          "requires": {
            "isarray": "0.0.1"
          }
        }
      }
    },
    "extend": {
      "version": "3.0.2",
      "resolved": "https://registry.npmjs.org/extend/-/extend-3.0.2.tgz",
      "integrity": "sha512-fjquC59cD7CyW6urNXK0FBufkZcoiGG80wTuPujX590cB5Ttln20E2UB4S/WARVqhXffZl2LNgS+gQdPIIim/g==",
      "dev": true
    },
    "external-editor": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/external-editor/-/external-editor-3.1.0.tgz",
      "integrity": "sha512-hMQ4CX1p1izmuLYyZqLMO/qGNw10wSv9QDCPfzXfyFrOaCSSoRfqE1Kf1s5an66J5JZC62NewG+mK49jOCtQew==",
      "dev": true,
      "requires": {
        "chardet": "^0.7.0",
        "iconv-lite": "^0.4.24",
        "tmp": "^0.0.33"
      }
    },
    "fast-deep-equal": {
      "version": "3.1.3",
      "resolved": "https://registry.npmjs.org/fast-deep-equal/-/fast-deep-equal-3.1.3.tgz",
      "integrity": "sha512-f3qQ9oQy9j2AhBe/H9VC91wLmKBCCU/gDOnKNAYG5hswO7BLKj09Hc5HYNz9cGI++xlpDCIgDaitVs03ATR84Q==",
      "dev": true
    },
    "fast-glob": {
      "version": "3.2.11",
      "resolved": "https://registry.npmjs.org/fast-glob/-/fast-glob-3.2.11.tgz",
      "integrity": "sha512-xrO3+1bxSo3ZVHAnqzyuewYT6aMFHRAd4Kcs92MAonjwQZLsK9d0SF1IyQ3k5PoirxTW0Oe/RqFgMQ6TcNE5Ew==",
      "dev": true,
      "requires": {
        "@nodelib/fs.stat": "^2.0.2",
        "@nodelib/fs.walk": "^1.2.3",
        "glob-parent": "^5.1.2",
        "merge2": "^1.3.0",
        "micromatch": "^4.0.4"
      }
    },
    "fast-json-stable-stringify": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/fast-json-stable-stringify/-/fast-json-stable-stringify-2.1.0.tgz",
      "integrity": "sha512-lhd/wF+Lk98HZoTCtlVraHtfh5XYijIjalXck7saUtuanSDyLMxnHhSXEDJqHxD7msR8D0uCmqlkwjCV8xvwHw==",
      "dev": true
    },
    "fastq": {
      "version": "1.13.0",
      "resolved": "https://registry.npmjs.org/fastq/-/fastq-1.13.0.tgz",
      "integrity": "sha512-YpkpUnK8od0o1hmeSc7UUs/eB/vIPWJYjKck2QKIzAf71Vm1AAQ3EbuZB3g2JIy+pg+ERD0vqI79KyZiB2e2Nw==",
      "dev": true,
      "requires": {
        "reusify": "^1.0.4"
      }
    },
    "faye-websocket": {
      "version": "0.11.4",
      "resolved": "https://registry.npmjs.org/faye-websocket/-/faye-websocket-0.11.4.tgz",
      "integrity": "sha512-CzbClwlXAuiRQAlUyfqPgvPoNKTckTPGfwZV4ZdAhVcP2lh9KUxJg2b5GkE7XbjKQ3YJnQ9z6D9ntLAlB+tP8g==",
      "dev": true,
      "requires": {
        "websocket-driver": ">=0.5.1"
      }
    },
    "figures": {
      "version": "3.2.0",
      "resolved": "https://registry.npmjs.org/figures/-/figures-3.2.0.tgz",
      "integrity": "sha512-yaduQFRKLXYOGgEn6AZau90j3ggSOyiqXU0F9JZfeXYhNa+Jk4X+s45A2zg5jns87GAFa34BBm2kXw4XpNcbdg==",
      "dev": true,
      "requires": {
        "escape-string-regexp": "^1.0.5"
      }
    },
    "fill-range": {
      "version": "7.0.1",
      "resolved": "https://registry.npmjs.org/fill-range/-/fill-range-7.0.1.tgz",
      "integrity": "sha512-qOo9F+dMUmC2Lcb4BbVvnKJxTPjCm+RRpe4gDuGrzkL7mEVl/djYSu2OdQ2Pa302N4oqkSg9ir6jaLWJ2USVpQ==",
      "dev": true,
      "requires": {
        "to-regex-range": "^5.0.1"
      }
    },
    "finalhandler": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/finalhandler/-/finalhandler-1.1.2.tgz",
      "integrity": "sha512-aAWcW57uxVNrQZqFXjITpW3sIUQmHGG3qSb9mUah9MgMC4NeWhNOlNjXEYq3HjRAvL6arUviZGGJsBg6z0zsWA==",
      "requires": {
        "debug": "2.6.9",
        "encodeurl": "~1.0.2",
        "escape-html": "~1.0.3",
        "on-finished": "~2.3.0",
        "parseurl": "~1.3.3",
        "statuses": "~1.5.0",
        "unpipe": "~1.0.0"
      },
      "dependencies": {
        "debug": {
          "version": "2.6.9",
          "resolved": "https://registry.npmjs.org/debug/-/debug-2.6.9.tgz",
          "integrity": "sha512-bC7ElrdJaJnPbAP+1EotYvqZsb3ecl5wi6Bfi6BJTUcNowp6cvspg0jXznRTKDjm/E7AdgFBVeAPVMNcKGsHMA==",
          "requires": {
            "ms": "2.0.0"
          }
        },
        "ms": {
          "version": "2.0.0",
          "resolved": "https://registry.npmjs.org/ms/-/ms-2.0.0.tgz",
          "integrity": "sha1-VgiurfwAvmwpAd9fmGF4jeDVl8g="
        }
      }
    },
    "find-cache-dir": {
      "version": "3.3.2",
      "resolved": "https://registry.npmjs.org/find-cache-dir/-/find-cache-dir-3.3.2.tgz",
      "integrity": "sha512-wXZV5emFEjrridIgED11OoUKLxiYjAcqot/NJdAkOhlJ+vGzwhOAfcG5OX1jP+S0PcjEn8bdMJv+g2jwQ3Onig==",
      "dev": true,
      "requires": {
        "commondir": "^1.0.1",
        "make-dir": "^3.0.2",
        "pkg-dir": "^4.1.0"
      }
    },
    "find-up": {
      "version": "4.1.0",
      "resolved": "https://registry.npmjs.org/find-up/-/find-up-4.1.0.tgz",
      "integrity": "sha512-PpOwAdQ/YlXQ2vj8a3h8IipDuYRi3wceVQQGYWxNINccq40Anw7BlsEXCMbt1Zt+OLA6Fq9suIpIWD0OsnISlw==",
      "dev": true,
      "requires": {
        "locate-path": "^5.0.0",
        "path-exists": "^4.0.0"
      }
    },
    "flatted": {
      "version": "3.2.5",
      "resolved": "https://registry.npmjs.org/flatted/-/flatted-3.2.5.tgz",
      "integrity": "sha512-WIWGi2L3DyTUvUrwRKgGi9TwxQMUEqPOPQBVi71R96jZXJdFskXEmf54BoZaS1kknGODoIGASGEzBUYdyMCBJg==",
      "dev": true
    },
    "follow-redirects": {
      "version": "1.14.7",
      "resolved": "https://registry.npmjs.org/follow-redirects/-/follow-redirects-1.14.7.tgz",
      "integrity": "sha512-+hbxoLbFMbRKDwohX8GkTataGqO6Jb7jGwpAlwgy2bIz25XtRm7KEzJM76R1WiNT5SwZkX4Y75SwBolkpmE7iQ==",
      "dev": true
    },
    "forwarded": {
      "version": "0.2.0",
      "resolved": "https://registry.npmjs.org/forwarded/-/forwarded-0.2.0.tgz",
      "integrity": "sha512-buRG0fpBtRHSTCOASe6hD258tEubFoRLb4ZNA6NxMVHNw2gOcwHo9wyablzMzOA5z9xA9L1KNjk/Nt6MT9aYow=="
    },
    "fraction.js": {
      "version": "4.1.2",
      "resolved": "https://registry.npmjs.org/fraction.js/-/fraction.js-4.1.2.tgz",
      "integrity": "sha512-o2RiJQ6DZaR/5+Si0qJUIy637QMRudSi9kU/FFzx9EZazrIdnBgpU+3sEWCxAVhH2RtxW2Oz+T4p2o8uOPVcgA==",
      "dev": true
    },
    "fresh": {
      "version": "0.5.2",
      "resolved": "https://registry.npmjs.org/fresh/-/fresh-0.5.2.tgz",
      "integrity": "sha1-PYyt2Q2XZWn6g1qx+OSyOhBWBac="
    },
    "fs-extra": {
      "version": "10.0.0",
      "resolved": "https://registry.npmjs.org/fs-extra/-/fs-extra-10.0.0.tgz",
      "integrity": "sha512-C5owb14u9eJwizKGdchcDUQeFtlSHHthBk8pbX9Vc1PFZrLombudjDnNns88aYslCyF6IY5SUw3Roz6xShcEIQ==",
      "dev": true,
      "requires": {
        "graceful-fs": "^4.2.0",
        "jsonfile": "^6.0.1",
        "universalify": "^2.0.0"
      }
    },
    "fs-minipass": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/fs-minipass/-/fs-minipass-2.1.0.tgz",
      "integrity": "sha512-V/JgOLFCS+R6Vcq0slCuaeWEdNC3ouDlJMNIsacH2VtALiu9mV4LPrHc5cDl8k5aw6J8jwgWWpiTo5RYhmIzvg==",
      "dev": true,
      "requires": {
        "minipass": "^3.0.0"
      }
    },
    "fs-monkey": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/fs-monkey/-/fs-monkey-1.0.3.tgz",
      "integrity": "sha512-cybjIfiiE+pTWicSCLFHSrXZ6EilF30oh91FDP9S2B051prEa7QWfrVTQm10/dDpswBDXZugPa1Ogu8Yh+HV0Q==",
      "dev": true
    },
    "fs.realpath": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/fs.realpath/-/fs.realpath-1.0.0.tgz",
      "integrity": "sha1-FQStJSMVjKpA20onh8sBQRmU6k8=",
      "dev": true
    },
    "fsevents": {
      "version": "2.3.2",
      "resolved": "https://registry.npmjs.org/fsevents/-/fsevents-2.3.2.tgz",
      "integrity": "sha512-xiqMQR4xAeHTuB9uWm+fFRcIOgKBMiOBP+eXiyT7jsgVCq1bkVygt00oASowB7EdtpOHaaPgKt812P9ab+DDKA==",
      "dev": true,
      "optional": true
    },
    "function-bind": {
      "version": "1.1.1",
      "resolved": "https://registry.npmjs.org/function-bind/-/function-bind-1.1.1.tgz",
      "integrity": "sha512-yIovAzMX49sF8Yl58fSCWJ5svSLuaibPxXQJFLmBObTuCr0Mf1KiPopGM9NiFjiYBCbfaa2Fh6breQ6ANVTI0A==",
      "dev": true
    },
    "gauge": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/gauge/-/gauge-4.0.0.tgz",
      "integrity": "sha512-F8sU45yQpjQjxKkm1UOAhf0U/O0aFt//Fl7hsrNVto+patMHjs7dPI9mFOGUKbhrgKm0S3EjW3scMFuQmWSROw==",
      "dev": true,
      "requires": {
        "ansi-regex": "^5.0.1",
        "aproba": "^1.0.3 || ^2.0.0",
        "color-support": "^1.1.2",
        "console-control-strings": "^1.0.0",
        "has-unicode": "^2.0.1",
        "signal-exit": "^3.0.0",
        "string-width": "^4.2.3",
        "strip-ansi": "^6.0.1",
        "wide-align": "^1.1.2"
      }
    },
    "gensync": {
      "version": "1.0.0-beta.2",
      "resolved": "https://registry.npmjs.org/gensync/-/gensync-1.0.0-beta.2.tgz",
      "integrity": "sha512-3hN7NaskYvMDLQY55gnW3NQ+mesEAepTqlg+VEbj7zzqEMBVNhzcGYYeqFo/TlYz6eQiFcp1HcsCZO+nGgS8zg==",
      "dev": true
    },
    "get-caller-file": {
      "version": "2.0.5",
      "resolved": "https://registry.npmjs.org/get-caller-file/-/get-caller-file-2.0.5.tgz",
      "integrity": "sha512-DyFP3BM/3YHTQOCUL/w0OZHR0lpKeGrxotcHWcqNEdnltqFwXVfhEBQ94eIo34AfQpo0rGki4cyIiftY06h2Fg=="
    },
    "get-intrinsic": {
      "version": "1.1.1",
      "resolved": "https://registry.npmjs.org/get-intrinsic/-/get-intrinsic-1.1.1.tgz",
      "integrity": "sha512-kWZrnVM42QCiEA2Ig1bG8zjoIMOgxWwYCEeNdwY6Tv/cOSeGpcoX4pXHfKUxNKVoArnrEr2e9srnAxxGIraS9Q==",
      "dev": true,
      "requires": {
        "function-bind": "^1.1.1",
        "has": "^1.0.3",
        "has-symbols": "^1.0.1"
      }
    },
    "get-package-type": {
      "version": "0.1.0",
      "resolved": "https://registry.npmjs.org/get-package-type/-/get-package-type-0.1.0.tgz",
      "integrity": "sha512-pjzuKtY64GYfWizNAJ0fr9VqttZkNiK2iS430LtIHzjBEr6bX8Am2zm4sW4Ro5wjWW5cAlRL1qAMTcXbjNAO2Q==",
      "dev": true
    },
    "get-stream": {
      "version": "6.0.1",
      "resolved": "https://registry.npmjs.org/get-stream/-/get-stream-6.0.1.tgz",
      "integrity": "sha512-ts6Wi+2j3jQjqi70w5AlN8DFnkSwC+MqmxEzdEALB2qXZYV3X/b1CTfgPLGJNMeAWxdPfU8FO1ms3NUfaHCPYg==",
      "dev": true
    },
    "glob": {
      "version": "7.2.0",
      "resolved": "https://registry.npmjs.org/glob/-/glob-7.2.0.tgz",
      "integrity": "sha512-lmLf6gtyrPq8tTjSmrO94wBeQbFR3HbLHbuyD69wuyQkImp2hWqMGB47OX65FBkPffO641IP9jWa1z4ivqG26Q==",
      "dev": true,
      "requires": {
        "fs.realpath": "^1.0.0",
        "inflight": "^1.0.4",
        "inherits": "2",
        "minimatch": "^3.0.4",
        "once": "^1.3.0",
        "path-is-absolute": "^1.0.0"
      }
    },
    "glob-parent": {
      "version": "5.1.2",
      "resolved": "https://registry.npmjs.org/glob-parent/-/glob-parent-5.1.2.tgz",
      "integrity": "sha512-AOIgSQCepiJYwP3ARnGx+5VnTu2HBYdzbGP45eLw1vr3zB3vZLeyed1sC9hnbcOc9/SrMyM5RPQrkGz4aS9Zow==",
      "dev": true,
      "requires": {
        "is-glob": "^4.0.1"
      }
    },
    "glob-to-regexp": {
      "version": "0.4.1",
      "resolved": "https://registry.npmjs.org/glob-to-regexp/-/glob-to-regexp-0.4.1.tgz",
      "integrity": "sha512-lkX1HJXwyMcprw/5YUZc2s7DrpAiHB21/V+E1rHUrVNokkvB6bqMzT0VfV6/86ZNabt1k14YOIaT7nDvOX3Iiw==",
      "dev": true
    },
    "global-dirs": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/global-dirs/-/global-dirs-3.0.0.tgz",
      "integrity": "sha512-v8ho2DS5RiCjftj1nD9NmnfaOzTdud7RRnVd9kFNOjqZbISlx5DQ+OrTkywgd0dIt7oFCvKetZSHoHcP3sDdiA==",
      "requires": {
        "ini": "2.0.0"
      }
    },
    "globals": {
      "version": "11.12.0",
      "resolved": "https://registry.npmjs.org/globals/-/globals-11.12.0.tgz",
      "integrity": "sha512-WOBp/EEGUiIsJSp7wcv/y6MO+lV9UoncWqxuFfm8eBwzWNgyfBd6Gz+IeKQ9jCmyhoH99g15M3T+QaVHFjizVA==",
      "dev": true
    },
    "globby": {
      "version": "12.2.0",
      "resolved": "https://registry.npmjs.org/globby/-/globby-12.2.0.tgz",
      "integrity": "sha512-wiSuFQLZ+urS9x2gGPl1H5drc5twabmm4m2gTR27XDFyjUHJUNsS8o/2aKyIF6IoBaR630atdher0XJ5g6OMmA==",
      "dev": true,
      "requires": {
        "array-union": "^3.0.1",
        "dir-glob": "^3.0.1",
        "fast-glob": "^3.2.7",
        "ignore": "^5.1.9",
        "merge2": "^1.4.1",
        "slash": "^4.0.0"
      }
    },
    "got": {
      "version": "9.6.0",
      "resolved": "https://registry.npmjs.org/got/-/got-9.6.0.tgz",
      "integrity": "sha512-R7eWptXuGYxwijs0eV+v3o6+XH1IqVK8dJOEecQfTmkncw9AV4dcw/Dhxi8MdlqPthxxpZyizMzyg8RTmEsG+Q==",
      "requires": {
        "@sindresorhus/is": "^0.14.0",
        "@szmarczak/http-timer": "^1.1.2",
        "cacheable-request": "^6.0.0",
        "decompress-response": "^3.3.0",
        "duplexer3": "^0.1.4",
        "get-stream": "^4.1.0",
        "lowercase-keys": "^1.0.1",
        "mimic-response": "^1.0.1",
        "p-cancelable": "^1.0.0",
        "to-readable-stream": "^1.0.0",
        "url-parse-lax": "^3.0.0"
      },
      "dependencies": {
        "get-stream": {
          "version": "4.1.0",
          "resolved": "https://registry.npmjs.org/get-stream/-/get-stream-4.1.0.tgz",
          "integrity": "sha512-GMat4EJ5161kIy2HevLlr4luNjBgvmj413KaQA7jt4V8B4RDsfpHk7WQ9GVqfYyyx8OS/L66Kox+rJRNklLK7w==",
          "requires": {
            "pump": "^3.0.0"
          }
        }
      }
    },
    "graceful-fs": {
      "version": "4.2.9",
      "resolved": "https://registry.npmjs.org/graceful-fs/-/graceful-fs-4.2.9.tgz",
      "integrity": "sha512-NtNxqUcXgpW2iMrfqSfR73Glt39K+BLwWsPs94yR63v45T0Wbej7eRmL5cWfwEgqXnmjQp3zaJTshdRW/qC2ZQ=="
    },
    "handle-thing": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/handle-thing/-/handle-thing-2.0.1.tgz",
      "integrity": "sha512-9Qn4yBxelxoh2Ow62nP+Ka/kMnOXRi8BXnRaUwezLNhqelnN49xKz4F/dPP8OYLxLxq6JDtZb2i9XznUQbNPTg==",
      "dev": true
    },
    "has": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/has/-/has-1.0.3.tgz",
      "integrity": "sha512-f2dvO0VU6Oej7RkWJGrehjbzMAjFp5/VKPp5tTpWIV4JHHZK1/BxbFRtf/siA2SWTe09caDmVtYYzWEIbBS4zw==",
      "dev": true,
      "requires": {
        "function-bind": "^1.1.1"
      }
    },
    "has-flag": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/has-flag/-/has-flag-3.0.0.tgz",
      "integrity": "sha1-tdRU3CGZriJWmfNGfloH87lVuv0=",
      "dev": true
    },
    "has-symbols": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/has-symbols/-/has-symbols-1.0.2.tgz",
      "integrity": "sha512-chXa79rL/UC2KlX17jo3vRGz0azaWEx5tGqZg5pO3NUyEJVB17dMruQlzCCOfUvElghKcm5194+BCRvi2Rv/Gw==",
      "dev": true
    },
    "has-tostringtag": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/has-tostringtag/-/has-tostringtag-1.0.0.tgz",
      "integrity": "sha512-kFjcSNhnlGV1kyoGk7OXKSawH5JOb/LzUc5w9B02hOTO0dfFRjbHQKvg1d6cf3HbeUmtU9VbbV3qzZ2Teh97WQ==",
      "dev": true,
      "requires": {
        "has-symbols": "^1.0.2"
      }
    },
    "has-unicode": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/has-unicode/-/has-unicode-2.0.1.tgz",
      "integrity": "sha1-4Ob+aijPUROIVeCG0Wkedx3iqLk=",
      "dev": true
    },
    "has-yarn": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/has-yarn/-/has-yarn-2.1.0.tgz",
      "integrity": "sha512-UqBRqi4ju7T+TqGNdqAO0PaSVGsDGJUBQvk9eUWNGRY1CFGDzYhLWoM7JQEemnlvVcv/YEmc2wNW8BC24EnUsw=="
    },
    "hdr-histogram-js": {
      "version": "2.0.3",
      "resolved": "https://registry.npmjs.org/hdr-histogram-js/-/hdr-histogram-js-2.0.3.tgz",
      "integrity": "sha512-Hkn78wwzWHNCp2uarhzQ2SGFLU3JY8SBDDd3TAABK4fc30wm+MuPOrg5QVFVfkKOQd6Bfz3ukJEI+q9sXEkK1g==",
      "dev": true,
      "requires": {
        "@assemblyscript/loader": "^0.10.1",
        "base64-js": "^1.2.0",
        "pako": "^1.0.3"
      }
    },
    "hdr-histogram-percentiles-obj": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/hdr-histogram-percentiles-obj/-/hdr-histogram-percentiles-obj-3.0.0.tgz",
      "integrity": "sha512-7kIufnBqdsBGcSZLPJwqHT3yhk1QTsSlFsVD3kx5ixH/AlgBs9yM1q6DPhXZ8f8gtdqgh7N7/5btRLpQsS2gHw==",
      "dev": true
    },
    "hosted-git-info": {
      "version": "4.1.0",
      "resolved": "https://registry.npmjs.org/hosted-git-info/-/hosted-git-info-4.1.0.tgz",
      "integrity": "sha512-kyCuEOWjJqZuDbRHzL8V93NzQhwIB71oFWSyzVo+KPZI+pnQPPxucdkrOZvkLRnrf5URsQM+IJ09Dw29cRALIA==",
      "dev": true,
      "requires": {
        "lru-cache": "^6.0.0"
      }
    },
    "hpack.js": {
      "version": "2.1.6",
      "resolved": "https://registry.npmjs.org/hpack.js/-/hpack.js-2.1.6.tgz",
      "integrity": "sha1-h3dMCUnlE/QuhFdbPEVoH63ioLI=",
      "dev": true,
      "requires": {
        "inherits": "^2.0.1",
        "obuf": "^1.0.0",
        "readable-stream": "^2.0.1",
        "wbuf": "^1.1.0"
      },
      "dependencies": {
        "readable-stream": {
          "version": "2.3.7",
          "resolved": "https://registry.npmjs.org/readable-stream/-/readable-stream-2.3.7.tgz",
          "integrity": "sha512-Ebho8K4jIbHAxnuxi7o42OrZgF/ZTNcsZj6nRKyUmkhLFq8CHItp/fy6hQZuZmP/n3yZ9VBUbp4zz/mX8hmYPw==",
          "dev": true,
          "requires": {
            "core-util-is": "~1.0.0",
            "inherits": "~2.0.3",
            "isarray": "~1.0.0",
            "process-nextick-args": "~2.0.0",
            "safe-buffer": "~5.1.1",
            "string_decoder": "~1.1.1",
            "util-deprecate": "~1.0.1"
          }
        },
        "string_decoder": {
          "version": "1.1.1",
          "resolved": "https://registry.npmjs.org/string_decoder/-/string_decoder-1.1.1.tgz",
          "integrity": "sha512-n/ShnvDi6FHbbVfviro+WojiFzv+s8MPMHBczVePfUpDJLwoLT0ht1l4YwBCbi8pJAveEEdnkHyPyTP/mzRfwg==",
          "dev": true,
          "requires": {
            "safe-buffer": "~5.1.0"
          }
        }
      }
    },
    "html-entities": {
      "version": "2.3.2",
      "resolved": "https://registry.npmjs.org/html-entities/-/html-entities-2.3.2.tgz",
      "integrity": "sha512-c3Ab/url5ksaT0WyleslpBEthOzWhrjQbg75y7XUsfSzi3Dgzt0l8w5e7DylRn15MTlMMD58dTfzddNS2kcAjQ==",
      "dev": true
    },
    "html-escaper": {
      "version": "2.0.2",
      "resolved": "https://registry.npmjs.org/html-escaper/-/html-escaper-2.0.2.tgz",
      "integrity": "sha512-H2iMtd0I4Mt5eYiapRdIDjp+XzelXQ0tFE4JS7YFwFevXXMmOp9myNrUvCg0D6ws8iqkRPBfKHgbwig1SmlLfg==",
      "dev": true
    },
    "http-cache-semantics": {
      "version": "4.1.0",
      "resolved": "https://registry.npmjs.org/http-cache-semantics/-/http-cache-semantics-4.1.0.tgz",
      "integrity": "sha512-carPklcUh7ROWRK7Cv27RPtdhYhUsela/ue5/jKzjegVvXDqM2ILE9Q2BGn9JZJh1g87cp56su/FgQSzcWS8cQ=="
    },
    "http-deceiver": {
      "version": "1.2.7",
      "resolved": "https://registry.npmjs.org/http-deceiver/-/http-deceiver-1.2.7.tgz",
      "integrity": "sha1-+nFolEq5pRnTN8sL7HKE3D5yPYc=",
      "dev": true
    },
    "http-errors": {
      "version": "1.8.1",
      "resolved": "https://registry.npmjs.org/http-errors/-/http-errors-1.8.1.tgz",
      "integrity": "sha512-Kpk9Sm7NmI+RHhnj6OIWDI1d6fIoFAtFt9RLaTMRlg/8w49juAStsrBgp0Dp4OdxdVbRIeKhtCUvoi/RuAhO4g==",
      "requires": {
        "depd": "~1.1.2",
        "inherits": "2.0.4",
        "setprototypeof": "1.2.0",
        "statuses": ">= 1.5.0 < 2",
        "toidentifier": "1.0.1"
      }
    },
    "http-parser-js": {
      "version": "0.5.5",
      "resolved": "https://registry.npmjs.org/http-parser-js/-/http-parser-js-0.5.5.tgz",
      "integrity": "sha512-x+JVEkO2PoM8qqpbPbOL3cqHPwerep7OwzK7Ay+sMQjKzaKCqWvjoXm5tqMP9tXWWTnTzAjIhXg+J99XYuPhPA==",
      "dev": true
    },
    "http-proxy": {
      "version": "1.18.1",
      "resolved": "https://registry.npmjs.org/http-proxy/-/http-proxy-1.18.1.tgz",
      "integrity": "sha512-7mz/721AbnJwIVbnaSv1Cz3Am0ZLT/UBwkC92VlxhXv/k/BBQfM2fXElQNC27BVGr0uwUpplYPQM9LnaBMR5NQ==",
      "dev": true,
      "requires": {
        "eventemitter3": "^4.0.0",
        "follow-redirects": "^1.0.0",
        "requires-port": "^1.0.0"
      }
    },
    "http-proxy-agent": {
      "version": "4.0.1",
      "resolved": "https://registry.npmjs.org/http-proxy-agent/-/http-proxy-agent-4.0.1.tgz",
      "integrity": "sha512-k0zdNgqWTGA6aeIRVpvfVob4fL52dTfaehylg0Y4UvSySvOq/Y+BOyPrgpUrA7HylqvU8vIZGsRuXmspskV0Tg==",
      "dev": true,
      "requires": {
        "@tootallnate/once": "1",
        "agent-base": "6",
        "debug": "4"
      }
    },
    "http-proxy-middleware": {
      "version": "2.0.2",
      "resolved": "https://registry.npmjs.org/http-proxy-middleware/-/http-proxy-middleware-2.0.2.tgz",
      "integrity": "sha512-XtmDN5w+vdFTBZaYhdJAbMqn0DP/EhkUaAeo963mojwpKMMbw6nivtFKw07D7DDOH745L5k0VL0P8KRYNEVF/g==",
      "dev": true,
      "requires": {
        "@types/http-proxy": "^1.17.8",
        "http-proxy": "^1.18.1",
        "is-glob": "^4.0.1",
        "is-plain-obj": "^3.0.0",
        "micromatch": "^4.0.2"
      }
    },
    "https-proxy-agent": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/https-proxy-agent/-/https-proxy-agent-5.0.0.tgz",
      "integrity": "sha512-EkYm5BcKUGiduxzSt3Eppko+PiNWNEpa4ySk9vTC6wDsQJW9rHSa+UhGNJoRYp7bz6Ht1eaRIa6QaJqO5rCFbA==",
      "dev": true,
      "requires": {
        "agent-base": "6",
        "debug": "4"
      }
    },
    "human-signals": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/human-signals/-/human-signals-2.1.0.tgz",
      "integrity": "sha512-B4FFZ6q/T2jhhksgkbEW3HBvWIfDW85snkQgawt07S7J5QXTk6BkNV+0yAeZrM5QpMAdYlocGoljn0sJ/WQkFw==",
      "dev": true
    },
    "humanize-ms": {
      "version": "1.2.1",
      "resolved": "https://registry.npmjs.org/humanize-ms/-/humanize-ms-1.2.1.tgz",
      "integrity": "sha1-xG4xWaKT9riW2ikxbYtv6Lt5u+0=",
      "dev": true,
      "requires": {
        "ms": "^2.0.0"
      }
    },
    "iconv-lite": {
      "version": "0.4.24",
      "resolved": "https://registry.npmjs.org/iconv-lite/-/iconv-lite-0.4.24.tgz",
      "integrity": "sha512-v3MXnZAcvnywkTUEZomIActle7RXXeedOR31wwl7VlyoXO4Qi9arvSenNQWne1TcRwhCL1HwLI21bEqdpj8/rA==",
      "requires": {
        "safer-buffer": ">= 2.1.2 < 3"
      }
    },
    "icss-utils": {
      "version": "5.1.0",
      "resolved": "https://registry.npmjs.org/icss-utils/-/icss-utils-5.1.0.tgz",
      "integrity": "sha512-soFhflCVWLfRNOPU3iv5Z9VUdT44xFRbzjLsEzSr5AQmgqPMTHdU3PMT1Cf1ssx8fLNJDA1juftYl+PUcv3MqA==",
      "dev": true,
      "requires": {}
    },
    "ieee754": {
      "version": "1.2.1",
      "resolved": "https://registry.npmjs.org/ieee754/-/ieee754-1.2.1.tgz",
      "integrity": "sha512-dcyqhDvX1C46lXZcVqCpK+FtMRQVdIMN6/Df5js2zouUsqG7I6sFxitIC+7KYK29KdXOLHdu9zL4sFnoVQnqaA==",
      "dev": true
    },
    "ignore": {
      "version": "5.2.0",
      "resolved": "https://registry.npmjs.org/ignore/-/ignore-5.2.0.tgz",
      "integrity": "sha512-CmxgYGiEPCLhfLnpPp1MoRmifwEIOgjcHXxOBjv7mY96c+eWScsOP9c112ZyLdWHi0FxHjI+4uVhKYp/gcdRmQ==",
      "dev": true
    },
    "ignore-walk": {
      "version": "4.0.1",
      "resolved": "https://registry.npmjs.org/ignore-walk/-/ignore-walk-4.0.1.tgz",
      "integrity": "sha512-rzDQLaW4jQbh2YrOFlJdCtX8qgJTehFRYiUB2r1osqTeDzV/3+Jh8fz1oAPzUThf3iku8Ds4IDqawI5d8mUiQw==",
      "dev": true,
      "requires": {
        "minimatch": "^3.0.4"
      }
    },
    "image-size": {
      "version": "0.5.5",
      "resolved": "https://registry.npmjs.org/image-size/-/image-size-0.5.5.tgz",
      "integrity": "sha1-Cd/Uq50g4p6xw+gLiZA3jfnjy5w=",
      "dev": true,
      "optional": true
    },
    "immutable": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/immutable/-/immutable-4.0.0.tgz",
      "integrity": "sha512-zIE9hX70qew5qTUjSS7wi1iwj/l7+m54KWU247nhM3v806UdGj1yDndXj+IOYxxtW9zyLI+xqFNZjTuDaLUqFw==",
      "dev": true
    },
    "import-fresh": {
      "version": "3.3.0",
      "resolved": "https://registry.npmjs.org/import-fresh/-/import-fresh-3.3.0.tgz",
      "integrity": "sha512-veYYhQa+D1QBKznvhUHxb8faxlrwUnxseDAbAp457E0wLNio2bOSKnjYDhMj+YiAq61xrMGhQk9iXVk5FzgQMw==",
      "dev": true,
      "requires": {
        "parent-module": "^1.0.0",
        "resolve-from": "^4.0.0"
      },
      "dependencies": {
        "resolve-from": {
          "version": "4.0.0",
          "resolved": "https://registry.npmjs.org/resolve-from/-/resolve-from-4.0.0.tgz",
          "integrity": "sha512-pb/MYmXstAkysRFx8piNI1tGFNQIFA3vkE3Gq4EuA1dF6gHp/+vgZqsCGJapvy8N3Q+4o7FwvquPJcnZ7RYy4g==",
          "dev": true
        }
      }
    },
    "import-lazy": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/import-lazy/-/import-lazy-2.1.0.tgz",
      "integrity": "sha1-BWmOPUXIjo1+nZLLBYTnfwlvPkM="
    },
    "imurmurhash": {
      "version": "0.1.4",
      "resolved": "https://registry.npmjs.org/imurmurhash/-/imurmurhash-0.1.4.tgz",
      "integrity": "sha1-khi5srkoojixPcT7a21XbyMUU+o="
    },
    "indent-string": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/indent-string/-/indent-string-4.0.0.tgz",
      "integrity": "sha512-EdDDZu4A2OyIK7Lr/2zG+w5jmbuk1DVBnEwREQvBzspBJkCEbRa8GxU1lghYcaGJCnRWibjDXlq779X1/y5xwg==",
      "dev": true
    },
    "infer-owner": {
      "version": "1.0.4",
      "resolved": "https://registry.npmjs.org/infer-owner/-/infer-owner-1.0.4.tgz",
      "integrity": "sha512-IClj+Xz94+d7irH5qRyfJonOdfTzuDaifE6ZPWfx0N0+/ATZCbuTPq2prFl526urkQd90WyUKIh1DfBQ2hMz9A==",
      "dev": true
    },
    "inflight": {
      "version": "1.0.6",
      "resolved": "https://registry.npmjs.org/inflight/-/inflight-1.0.6.tgz",
      "integrity": "sha1-Sb1jMdfQLQwJvJEKEHW6gWW1bfk=",
      "dev": true,
      "requires": {
        "once": "^1.3.0",
        "wrappy": "1"
      }
    },
    "inherits": {
      "version": "2.0.4",
      "resolved": "https://registry.npmjs.org/inherits/-/inherits-2.0.4.tgz",
      "integrity": "sha512-k/vGaX4/Yla3WzyMCvTQOXYeIHvqOKtnqBduzTHpzpQZzAskKMhZ2K+EnBiSM9zGSoIFeMpXKxa4dYeZIQqewQ=="
    },
    "ini": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/ini/-/ini-2.0.0.tgz",
      "integrity": "sha512-7PnF4oN3CvZF23ADhA5wRaYEQpJ8qygSkbtTXWBeXWXmEVRXK+1ITciHWwHhsjv1TmW0MgacIv6hEi5pX5NQdA=="
    },
    "inquirer": {
      "version": "8.2.0",
      "resolved": "https://registry.npmjs.org/inquirer/-/inquirer-8.2.0.tgz",
      "integrity": "sha512-0crLweprevJ02tTuA6ThpoAERAGyVILC4sS74uib58Xf/zSr1/ZWtmm7D5CI+bSQEaA04f0K7idaHpQbSWgiVQ==",
      "dev": true,
      "requires": {
        "ansi-escapes": "^4.2.1",
        "chalk": "^4.1.1",
        "cli-cursor": "^3.1.0",
        "cli-width": "^3.0.0",
        "external-editor": "^3.0.3",
        "figures": "^3.0.0",
        "lodash": "^4.17.21",
        "mute-stream": "0.0.8",
        "ora": "^5.4.1",
        "run-async": "^2.4.0",
        "rxjs": "^7.2.0",
        "string-width": "^4.1.0",
        "strip-ansi": "^6.0.0",
        "through": "^2.3.6"
      },
      "dependencies": {
        "ansi-styles": {
          "version": "4.3.0",
          "resolved": "https://registry.npmjs.org/ansi-styles/-/ansi-styles-4.3.0.tgz",
          "integrity": "sha512-zbB9rCJAT1rbjiVDb2hqKFHNYLxgtk8NURxZ3IZwD3F6NtxbXZQCnnSi1Lkx+IDohdPlFp222wVALIheZJQSEg==",
          "dev": true,
          "requires": {
            "color-convert": "^2.0.1"
          }
        },
        "chalk": {
          "version": "4.1.2",
          "resolved": "https://registry.npmjs.org/chalk/-/chalk-4.1.2.tgz",
          "integrity": "sha512-oKnbhFyRIXpUuez8iBMmyEa4nbj4IOQyuhc/wy9kY7/WVPcwIO9VA668Pu8RkO7+0G76SLROeyw9CpQ061i4mA==",
          "dev": true,
          "requires": {
            "ansi-styles": "^4.1.0",
            "supports-color": "^7.1.0"
          }
        },
        "color-convert": {
          "version": "2.0.1",
          "resolved": "https://registry.npmjs.org/color-convert/-/color-convert-2.0.1.tgz",
          "integrity": "sha512-RRECPsj7iu/xb5oKYcsFHSppFNnsj/52OVTRKb4zP5onXwVF3zVmmToNcOfGC+CRDpfK/U584fMg38ZHCaElKQ==",
          "dev": true,
          "requires": {
            "color-name": "~1.1.4"
          }
        },
        "color-name": {
          "version": "1.1.4",
          "resolved": "https://registry.npmjs.org/color-name/-/color-name-1.1.4.tgz",
          "integrity": "sha512-dOy+3AuW3a2wNbZHIuMZpTcgjGuLU/uBL/ubcZF9OXbDo8ff4O8yVp5Bf0efS8uEoYo5q4Fx7dY9OgQGXgAsQA==",
          "dev": true
        },
        "has-flag": {
          "version": "4.0.0",
          "resolved": "https://registry.npmjs.org/has-flag/-/has-flag-4.0.0.tgz",
          "integrity": "sha512-EykJT/Q1KjTWctppgIAgfSO0tKVuZUjhgMr17kqTumMl6Afv3EISleU7qZUzoXDFTAHTDC4NOoG/ZxU3EvlMPQ==",
          "dev": true
        },
        "supports-color": {
          "version": "7.2.0",
          "resolved": "https://registry.npmjs.org/supports-color/-/supports-color-7.2.0.tgz",
          "integrity": "sha512-qpCAvRl9stuOHveKsn7HncJRvv501qIacKzQlO/+Lwxc9+0q2wLyv4Dfvt80/DPn2pqOBsJdDiogXGR9+OvwRw==",
          "dev": true,
          "requires": {
            "has-flag": "^4.0.0"
          }
        }
      }
    },
    "ip": {
      "version": "1.1.5",
      "resolved": "https://registry.npmjs.org/ip/-/ip-1.1.5.tgz",
      "integrity": "sha1-vd7XARQpCCjAoDnnLvJfWq7ENUo=",
      "dev": true
    },
    "ipaddr.js": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/ipaddr.js/-/ipaddr.js-2.0.1.tgz",
      "integrity": "sha512-1qTgH9NG+IIJ4yfKs2e6Pp1bZg8wbDbKHT21HrLIeYBTRLgMYKnMTPAuI3Lcs61nfx5h1xlXnbJtH1kX5/d/ng==",
      "dev": true
    },
    "is-arguments": {
      "version": "1.1.1",
      "resolved": "https://registry.npmjs.org/is-arguments/-/is-arguments-1.1.1.tgz",
      "integrity": "sha512-8Q7EARjzEnKpt/PCD7e1cgUS0a6X8u5tdSiMqXhojOdoV9TsMsiO+9VLC5vAmO8N7/GmXn7yjR8qnA6bVAEzfA==",
      "dev": true,
      "requires": {
        "call-bind": "^1.0.2",
        "has-tostringtag": "^1.0.0"
      }
    },
    "is-arrayish": {
      "version": "0.2.1",
      "resolved": "https://registry.npmjs.org/is-arrayish/-/is-arrayish-0.2.1.tgz",
      "integrity": "sha1-d8mYQFJ6qOyxqLppe4BkWnqSap0=",
      "dev": true
    },
    "is-binary-path": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/is-binary-path/-/is-binary-path-2.1.0.tgz",
      "integrity": "sha512-ZMERYes6pDydyuGidse7OsHxtbI7WVeUEozgR/g7rd0xUimYNlvZRE/K2MgZTjWy725IfelLeVcEM97mmtRGXw==",
      "dev": true,
      "requires": {
        "binary-extensions": "^2.0.0"
      }
    },
    "is-ci": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/is-ci/-/is-ci-2.0.0.tgz",
      "integrity": "sha512-YfJT7rkpQB0updsdHLGWrvhBJfcfzNNawYDNIyQXJz0IViGf75O8EBPKSdvw2rF+LGCsX4FZ8tcr3b19LcZq4w==",
      "requires": {
        "ci-info": "^2.0.0"
      }
    },
    "is-core-module": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/is-core-module/-/is-core-module-2.8.1.tgz",
      "integrity": "sha512-SdNCUs284hr40hFTFP6l0IfZ/RSrMXF3qgoRHd3/79unUTvrFO/JoXwkGm+5J/Oe3E/b5GsnG330uUNgRpu1PA==",
      "dev": true,
      "requires": {
        "has": "^1.0.3"
      }
    },
    "is-date-object": {
      "version": "1.0.5",
      "resolved": "https://registry.npmjs.org/is-date-object/-/is-date-object-1.0.5.tgz",
      "integrity": "sha512-9YQaSxsAiSwcvS33MBk3wTCVnWK+HhF8VZR2jRxehM16QcVOdHqPn4VPHmRK4lSr38n9JriurInLcP90xsYNfQ==",
      "dev": true,
      "requires": {
        "has-tostringtag": "^1.0.0"
      }
    },
    "is-docker": {
      "version": "2.2.1",
      "resolved": "https://registry.npmjs.org/is-docker/-/is-docker-2.2.1.tgz",
      "integrity": "sha512-F+i2BKsFrH66iaUFc0woD8sLy8getkwTwtOBjvs56Cx4CgJDeKQeqfz8wAYiSb8JOprWhHH5p77PbmYCvvUuXQ==",
      "dev": true
    },
    "is-extglob": {
      "version": "2.1.1",
      "resolved": "https://registry.npmjs.org/is-extglob/-/is-extglob-2.1.1.tgz",
      "integrity": "sha1-qIwCU1eR8C7TfHahueqXc8gz+MI=",
      "dev": true
    },
    "is-fullwidth-code-point": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/is-fullwidth-code-point/-/is-fullwidth-code-point-3.0.0.tgz",
      "integrity": "sha512-zymm5+u+sCsSWyD9qNaejV3DFvhCKclKdizYaJUuHA83RLjb7nSuGnddCHGv0hk+KY7BMAlsWeK4Ueg6EV6XQg=="
    },
    "is-glob": {
      "version": "4.0.3",
      "resolved": "https://registry.npmjs.org/is-glob/-/is-glob-4.0.3.tgz",
      "integrity": "sha512-xelSayHH36ZgE7ZWhli7pW34hNbNl8Ojv5KVmkJD4hBdD3th8Tfk9vYasLM+mXWOZhFkgZfxhLSnrwRr4elSSg==",
      "dev": true,
      "requires": {
        "is-extglob": "^2.1.1"
      }
    },
    "is-installed-globally": {
      "version": "0.4.0",
      "resolved": "https://registry.npmjs.org/is-installed-globally/-/is-installed-globally-0.4.0.tgz",
      "integrity": "sha512-iwGqO3J21aaSkC7jWnHP/difazwS7SFeIqxv6wEtLU8Y5KlzFTjyqcSIT0d8s4+dDhKytsk9PJZ2BkS5eZwQRQ==",
      "requires": {
        "global-dirs": "^3.0.0",
        "is-path-inside": "^3.0.2"
      }
    },
    "is-interactive": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/is-interactive/-/is-interactive-1.0.0.tgz",
      "integrity": "sha512-2HvIEKRoqS62guEC+qBjpvRubdX910WCMuJTZ+I9yvqKU2/12eSL549HMwtabb4oupdj2sMP50k+XJfB/8JE6w==",
      "dev": true
    },
    "is-lambda": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/is-lambda/-/is-lambda-1.0.1.tgz",
      "integrity": "sha1-PZh3iZ5qU+/AFgUEzeFfgubwYdU=",
      "dev": true
    },
    "is-npm": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/is-npm/-/is-npm-5.0.0.tgz",
      "integrity": "sha512-WW/rQLOazUq+ST/bCAVBp/2oMERWLsR7OrKyt052dNDk4DHcDE0/7QSXITlmi+VBcV13DfIbysG3tZJm5RfdBA=="
    },
    "is-number": {
      "version": "7.0.0",
      "resolved": "https://registry.npmjs.org/is-number/-/is-number-7.0.0.tgz",
      "integrity": "sha512-41Cifkg6e8TylSpdtTpeLVMqvSBEVzTttHvERD741+pnZ8ANv0004MRL43QKPDlK9cGvNp6NZWZUBlbGXYxxng==",
      "dev": true
    },
    "is-obj": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/is-obj/-/is-obj-2.0.0.tgz",
      "integrity": "sha512-drqDG3cbczxxEJRoOXcOjtdp1J/lyp1mNn0xaznRs8+muBhgQcrnbspox5X5fOw0HnMnbfDzvnEMEtqDEJEo8w=="
    },
    "is-path-cwd": {
      "version": "2.2.0",
      "resolved": "https://registry.npmjs.org/is-path-cwd/-/is-path-cwd-2.2.0.tgz",
      "integrity": "sha512-w942bTcih8fdJPJmQHFzkS76NEP8Kzzvmw92cXsazb8intwLqPibPPdXf4ANdKV3rYMuuQYGIWtvz9JilB3NFQ==",
      "dev": true
    },
    "is-path-inside": {
      "version": "3.0.3",
      "resolved": "https://registry.npmjs.org/is-path-inside/-/is-path-inside-3.0.3.tgz",
      "integrity": "sha512-Fd4gABb+ycGAmKou8eMftCupSir5lRxqf4aD/vd0cD2qc4HL07OjCeuHMr8Ro4CoMaeCKDB0/ECBOVWjTwUvPQ=="
    },
    "is-plain-obj": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/is-plain-obj/-/is-plain-obj-3.0.0.tgz",
      "integrity": "sha512-gwsOE28k+23GP1B6vFl1oVh/WOzmawBrKwo5Ev6wMKzPkaXaCDIQKzLnvsA42DRlbVTWorkgTKIviAKCWkfUwA==",
      "dev": true
    },
    "is-plain-object": {
      "version": "2.0.4",
      "resolved": "https://registry.npmjs.org/is-plain-object/-/is-plain-object-2.0.4.tgz",
      "integrity": "sha512-h5PpgXkWitc38BBMYawTYMWJHFZJVnBquFE57xFpjB8pJFiF6gZ+bU+WyI/yqXiFR5mdLsgYNaPe8uao6Uv9Og==",
      "dev": true,
      "requires": {
        "isobject": "^3.0.1"
      }
    },
    "is-promise": {
      "version": "2.2.2",
      "resolved": "https://registry.npmjs.org/is-promise/-/is-promise-2.2.2.tgz",
      "integrity": "sha512-+lP4/6lKUBfQjZ2pdxThZvLUAafmZb8OAxFb8XXtiQmS35INgr85hdOGoEs124ez1FCnZJt6jau/T+alh58QFQ=="
    },
    "is-regex": {
      "version": "1.1.4",
      "resolved": "https://registry.npmjs.org/is-regex/-/is-regex-1.1.4.tgz",
      "integrity": "sha512-kvRdxDsxZjhzUX07ZnLydzS1TU/TJlTUHHY4YLL87e37oUA49DfkLqgy+VjFocowy29cKvcSiu+kIv728jTTVg==",
      "dev": true,
      "requires": {
        "call-bind": "^1.0.2",
        "has-tostringtag": "^1.0.0"
      }
    },
    "is-stream": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/is-stream/-/is-stream-2.0.1.tgz",
      "integrity": "sha512-hFoiJiTl63nn+kstHGBtewWSKnQLpyb155KHheA1l39uvtO9nWIop1p3udqPcUd/xbF1VLMO4n7OI6p7RbngDg==",
      "dev": true
    },
    "is-typedarray": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/is-typedarray/-/is-typedarray-1.0.0.tgz",
      "integrity": "sha1-5HnICFjfDBsR3dppQPlgEfzaSpo="
    },
    "is-unicode-supported": {
      "version": "0.1.0",
      "resolved": "https://registry.npmjs.org/is-unicode-supported/-/is-unicode-supported-0.1.0.tgz",
      "integrity": "sha512-knxG2q4UC3u8stRGyAVJCOdxFmv5DZiRcdlIaAQXAbSfJya+OhopNotLQrstBhququ4ZpuKbDc/8S6mgXgPFPw==",
      "dev": true
    },
    "is-what": {
      "version": "3.14.1",
      "resolved": "https://registry.npmjs.org/is-what/-/is-what-3.14.1.tgz",
      "integrity": "sha512-sNxgpk9793nzSs7bA6JQJGeIuRBQhAaNGG77kzYQgMkrID+lS6SlK07K5LaptscDlSaIgH+GPFzf+d75FVxozA==",
      "dev": true
    },
    "is-wsl": {
      "version": "2.2.0",
      "resolved": "https://registry.npmjs.org/is-wsl/-/is-wsl-2.2.0.tgz",
      "integrity": "sha512-fKzAra0rGJUUBwGBgNkHZuToZcn+TtXHpeCgmkMJMMYx1sQDYaCSyjJBSCa2nH1DGm7s3n1oBnohoVTBaN7Lww==",
      "dev": true,
      "requires": {
        "is-docker": "^2.0.0"
      }
    },
    "is-yarn-global": {
      "version": "0.3.0",
      "resolved": "https://registry.npmjs.org/is-yarn-global/-/is-yarn-global-0.3.0.tgz",
      "integrity": "sha512-VjSeb/lHmkoyd8ryPVIKvOCn4D1koMqY+vqyjjUfc3xyKtP4dYOxM44sZrnqQSzSds3xyOrUTLTC9LVCVgLngw=="
    },
    "isarray": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/isarray/-/isarray-1.0.0.tgz",
      "integrity": "sha1-u5NdSFgsuhaMBoNJV6VKPgcSTxE=",
      "dev": true
    },
    "isbinaryfile": {
      "version": "4.0.8",
      "resolved": "https://registry.npmjs.org/isbinaryfile/-/isbinaryfile-4.0.8.tgz",
      "integrity": "sha512-53h6XFniq77YdW+spoRrebh0mnmTxRPTlcuIArO57lmMdq4uBKFKaeTjnb92oYWrSn/LVL+LT+Hap2tFQj8V+w==",
      "dev": true
    },
    "isexe": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/isexe/-/isexe-2.0.0.tgz",
      "integrity": "sha1-6PvzdNxVb/iUehDcsFctYz8s+hA=",
      "dev": true
    },
    "isobject": {
      "version": "3.0.1",
      "resolved": "https://registry.npmjs.org/isobject/-/isobject-3.0.1.tgz",
      "integrity": "sha1-TkMekrEalzFjaqH5yNHMvP2reN8=",
      "dev": true
    },
    "istanbul-lib-coverage": {
      "version": "3.2.0",
      "resolved": "https://registry.npmjs.org/istanbul-lib-coverage/-/istanbul-lib-coverage-3.2.0.tgz",
      "integrity": "sha512-eOeJ5BHCmHYvQK7xt9GkdHuzuCGS1Y6g9Gvnx3Ym33fz/HpLRYxiS0wHNr+m/MBC8B647Xt608vCDEvhl9c6Mw==",
      "dev": true
    },
    "istanbul-lib-instrument": {
      "version": "5.1.0",
      "resolved": "https://registry.npmjs.org/istanbul-lib-instrument/-/istanbul-lib-instrument-5.1.0.tgz",
      "integrity": "sha512-czwUz525rkOFDJxfKK6mYfIs9zBKILyrZQxjz3ABhjQXhbhFsSbo1HW/BFcsDnfJYJWA6thRR5/TUY2qs5W99Q==",
      "dev": true,
      "requires": {
        "@babel/core": "^7.12.3",
        "@babel/parser": "^7.14.7",
        "@istanbuljs/schema": "^0.1.2",
        "istanbul-lib-coverage": "^3.2.0",
        "semver": "^6.3.0"
      },
      "dependencies": {
        "semver": {
          "version": "6.3.0",
          "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.0.tgz",
          "integrity": "sha512-b39TBaTSfV6yBrapU89p5fKekE2m/NwnDocOVruQFS1/veMgdzuPcnOM34M6CwxW8jH/lxEa5rBoDeUwu5HHTw==",
          "dev": true
        }
      }
    },
    "istanbul-lib-report": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/istanbul-lib-report/-/istanbul-lib-report-3.0.0.tgz",
      "integrity": "sha512-wcdi+uAKzfiGT2abPpKZ0hSU1rGQjUQnLvtY5MpQ7QCTahD3VODhcu4wcfY1YtkGaDD5yuydOLINXsfbus9ROw==",
      "dev": true,
      "requires": {
        "istanbul-lib-coverage": "^3.0.0",
        "make-dir": "^3.0.0",
        "supports-color": "^7.1.0"
      },
      "dependencies": {
        "has-flag": {
          "version": "4.0.0",
          "resolved": "https://registry.npmjs.org/has-flag/-/has-flag-4.0.0.tgz",
          "integrity": "sha512-EykJT/Q1KjTWctppgIAgfSO0tKVuZUjhgMr17kqTumMl6Afv3EISleU7qZUzoXDFTAHTDC4NOoG/ZxU3EvlMPQ==",
          "dev": true
        },
        "supports-color": {
          "version": "7.2.0",
          "resolved": "https://registry.npmjs.org/supports-color/-/supports-color-7.2.0.tgz",
          "integrity": "sha512-qpCAvRl9stuOHveKsn7HncJRvv501qIacKzQlO/+Lwxc9+0q2wLyv4Dfvt80/DPn2pqOBsJdDiogXGR9+OvwRw==",
          "dev": true,
          "requires": {
            "has-flag": "^4.0.0"
          }
        }
      }
    },
    "istanbul-lib-source-maps": {
      "version": "4.0.1",
      "resolved": "https://registry.npmjs.org/istanbul-lib-source-maps/-/istanbul-lib-source-maps-4.0.1.tgz",
      "integrity": "sha512-n3s8EwkdFIJCG3BPKBYvskgXGoy88ARzvegkitk60NxRdwltLOTaH7CUiMRXvwYorl0Q712iEjcWB+fK/MrWVw==",
      "dev": true,
      "requires": {
        "debug": "^4.1.1",
        "istanbul-lib-coverage": "^3.0.0",
        "source-map": "^0.6.1"
      },
      "dependencies": {
        "source-map": {
          "version": "0.6.1",
          "resolved": "https://registry.npmjs.org/source-map/-/source-map-0.6.1.tgz",
          "integrity": "sha512-UjgapumWlbMhkBgzT7Ykc5YXUT46F0iKu8SGXq0bcwP5dz/h0Plj6enJqjz1Zbq2l5WaqYnrVbwWOWMyF3F47g==",
          "dev": true
        }
      }
    },
    "istanbul-reports": {
      "version": "3.1.3",
      "resolved": "https://registry.npmjs.org/istanbul-reports/-/istanbul-reports-3.1.3.tgz",
      "integrity": "sha512-x9LtDVtfm/t1GFiLl3NffC7hz+I1ragvgX1P/Lg1NlIagifZDKUkuuaAxH/qpwj2IuEfD8G2Bs/UKp+sZ/pKkg==",
      "dev": true,
      "requires": {
        "html-escaper": "^2.0.0",
        "istanbul-lib-report": "^3.0.0"
      }
    },
    "jasmine-core": {
      "version": "3.10.1",
      "resolved": "https://registry.npmjs.org/jasmine-core/-/jasmine-core-3.10.1.tgz",
      "integrity": "sha512-ooZWSDVAdh79Rrj4/nnfklL3NQVra0BcuhcuWoAwwi+znLDoUeH87AFfeX8s+YeYi6xlv5nveRyaA1v7CintfA==",
      "dev": true
    },
    "jest-worker": {
      "version": "27.4.6",
      "resolved": "https://registry.npmjs.org/jest-worker/-/jest-worker-27.4.6.tgz",
      "integrity": "sha512-gHWJF/6Xi5CTG5QCvROr6GcmpIqNYpDJyc8A1h/DyXqH1tD6SnRCM0d3U5msV31D2LB/U+E0M+W4oyvKV44oNw==",
      "dev": true,
      "requires": {
        "@types/node": "*",
        "merge-stream": "^2.0.0",
        "supports-color": "^8.0.0"
      },
      "dependencies": {
        "has-flag": {
          "version": "4.0.0",
          "resolved": "https://registry.npmjs.org/has-flag/-/has-flag-4.0.0.tgz",
          "integrity": "sha512-EykJT/Q1KjTWctppgIAgfSO0tKVuZUjhgMr17kqTumMl6Afv3EISleU7qZUzoXDFTAHTDC4NOoG/ZxU3EvlMPQ==",
          "dev": true
        },
        "supports-color": {
          "version": "8.1.1",
          "resolved": "https://registry.npmjs.org/supports-color/-/supports-color-8.1.1.tgz",
          "integrity": "sha512-MpUEN2OodtUzxvKQl72cUF7RQ5EiHsGvSsVG0ia9c5RbWGL2CI4C7EpPS8UTBIplnlzZiNuV56w+FuNxy3ty2Q==",
          "dev": true,
          "requires": {
            "has-flag": "^4.0.0"
          }
        }
      }
    },
    "jju": {
      "version": "1.4.0",
      "resolved": "https://registry.npmjs.org/jju/-/jju-1.4.0.tgz",
      "integrity": "sha1-o6vicYryQaKykE+EpiWXDzia4yo="
    },
    "js-tokens": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/js-tokens/-/js-tokens-4.0.0.tgz",
      "integrity": "sha512-RdJUflcE3cUzKiMqQgsCu06FPu9UdIJO0beYbPhHN4k6apgJtifcoCtT9bcxOpYBtpD2kCM6Sbzg4CausW/PKQ==",
      "dev": true
    },
    "js-yaml": {
      "version": "3.14.1",
      "resolved": "https://registry.npmjs.org/js-yaml/-/js-yaml-3.14.1.tgz",
      "integrity": "sha512-okMH7OXXJ7YrN9Ok3/SXrnu4iX9yOk+25nqX4imS2npuvTYDmo/QEZoqwZkYaIDk3jVvBOTOIEgEhaLOynBS9g==",
      "dev": true,
      "requires": {
        "argparse": "^1.0.7",
        "esprima": "^4.0.0"
      }
    },
    "jsesc": {
      "version": "2.5.2",
      "resolved": "https://registry.npmjs.org/jsesc/-/jsesc-2.5.2.tgz",
      "integrity": "sha512-OYu7XEzjkCQ3C5Ps3QIZsQfNpqoJyZZA99wd9aWd05NCtC5pWOkShK2mkL6HXQR6/Cy2lbNdPlZBpuQHXE63gA==",
      "dev": true
    },
    "json-buffer": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/json-buffer/-/json-buffer-3.0.0.tgz",
      "integrity": "sha1-Wx85evx11ne96Lz8Dkfh+aPZqJg="
    },
    "json-parse-better-errors": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/json-parse-better-errors/-/json-parse-better-errors-1.0.2.tgz",
      "integrity": "sha512-mrqyZKfX5EhL7hvqcV6WG1yYjnjeuYDzDhhcAAUrq8Po85NBQBJP+ZDUT75qZQ98IkUoBqdkExkukOU7Ts2wrw==",
      "dev": true
    },
    "json-parse-even-better-errors": {
      "version": "2.3.1",
      "resolved": "https://registry.npmjs.org/json-parse-even-better-errors/-/json-parse-even-better-errors-2.3.1.tgz",
      "integrity": "sha512-xyFwyhro/JEof6Ghe2iz2NcXoj2sloNsWr/XsERDK/oiPCfaNhl5ONfp+jQdAZRQQ0IJWNzH9zIZF7li91kh2w==",
      "dev": true
    },
    "json-parse-helpfulerror": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/json-parse-helpfulerror/-/json-parse-helpfulerror-1.0.3.tgz",
      "integrity": "sha1-E/FM4C7tTpgSl7ZOueO5MuLdE9w=",
      "requires": {
        "jju": "^1.1.0"
      }
    },
    "json-schema-traverse": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/json-schema-traverse/-/json-schema-traverse-1.0.0.tgz",
      "integrity": "sha512-NM8/P9n3XjXhIZn1lLhkFaACTOURQXjWhV4BA/RnOv8xvgqtqpAX9IO4mRQxSx1Rlo4tqzeqb0sOlruaOy3dug==",
      "dev": true
    },
    "json-server": {
      "version": "0.17.0",
      "resolved": "https://registry.npmjs.org/json-server/-/json-server-0.17.0.tgz",
      "integrity": "sha512-+e/nW0mf666j1yTK+5dRx7hgxq5wJTkc5QhTYa/cBfD6vLlQWHfB4l8XKPgzeO55A8Hqm38g44OtZ5SooXi6MQ==",
      "requires": {
        "body-parser": "^1.19.0",
        "chalk": "^4.1.2",
        "compression": "^1.7.4",
        "connect-pause": "^0.1.1",
        "cors": "^2.8.5",
        "errorhandler": "^1.5.1",
        "express": "^4.17.1",
        "express-urlrewrite": "^1.4.0",
        "json-parse-helpfulerror": "^1.0.3",
        "lodash": "^4.17.21",
        "lodash-id": "^0.14.1",
        "lowdb": "^1.0.0",
        "method-override": "^3.0.0",
        "morgan": "^1.10.0",
        "nanoid": "^3.1.23",
        "please-upgrade-node": "^3.2.0",
        "pluralize": "^8.0.0",
        "server-destroy": "^1.0.1",
        "update-notifier": "^5.1.0",
        "yargs": "^17.0.1"
      },
      "dependencies": {
        "ansi-styles": {
          "version": "4.3.0",
          "resolved": "https://registry.npmjs.org/ansi-styles/-/ansi-styles-4.3.0.tgz",
          "integrity": "sha512-zbB9rCJAT1rbjiVDb2hqKFHNYLxgtk8NURxZ3IZwD3F6NtxbXZQCnnSi1Lkx+IDohdPlFp222wVALIheZJQSEg==",
          "requires": {
            "color-convert": "^2.0.1"
          }
        },
        "chalk": {
          "version": "4.1.2",
          "resolved": "https://registry.npmjs.org/chalk/-/chalk-4.1.2.tgz",
          "integrity": "sha512-oKnbhFyRIXpUuez8iBMmyEa4nbj4IOQyuhc/wy9kY7/WVPcwIO9VA668Pu8RkO7+0G76SLROeyw9CpQ061i4mA==",
          "requires": {
            "ansi-styles": "^4.1.0",
            "supports-color": "^7.1.0"
          }
        },
        "color-convert": {
          "version": "2.0.1",
          "resolved": "https://registry.npmjs.org/color-convert/-/color-convert-2.0.1.tgz",
          "integrity": "sha512-RRECPsj7iu/xb5oKYcsFHSppFNnsj/52OVTRKb4zP5onXwVF3zVmmToNcOfGC+CRDpfK/U584fMg38ZHCaElKQ==",
          "requires": {
            "color-name": "~1.1.4"
          }
        },
        "color-name": {
          "version": "1.1.4",
          "resolved": "https://registry.npmjs.org/color-name/-/color-name-1.1.4.tgz",
          "integrity": "sha512-dOy+3AuW3a2wNbZHIuMZpTcgjGuLU/uBL/ubcZF9OXbDo8ff4O8yVp5Bf0efS8uEoYo5q4Fx7dY9OgQGXgAsQA=="
        },
        "has-flag": {
          "version": "4.0.0",
          "resolved": "https://registry.npmjs.org/has-flag/-/has-flag-4.0.0.tgz",
          "integrity": "sha512-EykJT/Q1KjTWctppgIAgfSO0tKVuZUjhgMr17kqTumMl6Afv3EISleU7qZUzoXDFTAHTDC4NOoG/ZxU3EvlMPQ=="
        },
        "supports-color": {
          "version": "7.2.0",
          "resolved": "https://registry.npmjs.org/supports-color/-/supports-color-7.2.0.tgz",
          "integrity": "sha512-qpCAvRl9stuOHveKsn7HncJRvv501qIacKzQlO/+Lwxc9+0q2wLyv4Dfvt80/DPn2pqOBsJdDiogXGR9+OvwRw==",
          "requires": {
            "has-flag": "^4.0.0"
          }
        }
      }
    },
    "json5": {
      "version": "2.2.0",
      "resolved": "https://registry.npmjs.org/json5/-/json5-2.2.0.tgz",
      "integrity": "sha512-f+8cldu7X/y7RAJurMEJmdoKXGB/X550w2Nr3tTbezL6RwEE/iMcm+tZnXeoZtKuOq6ft8+CqzEkrIgx1fPoQA==",
      "dev": true,
      "requires": {
        "minimist": "^1.2.5"
      }
    },
    "jsonc-parser": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/jsonc-parser/-/jsonc-parser-3.0.0.tgz",
      "integrity": "sha512-fQzRfAbIBnR0IQvftw9FJveWiHp72Fg20giDrHz6TdfB12UH/uue0D3hm57UB5KgAVuniLMCaS8P1IMj9NR7cA==",
      "dev": true
    },
    "jsonfile": {
      "version": "6.1.0",
      "resolved": "https://registry.npmjs.org/jsonfile/-/jsonfile-6.1.0.tgz",
      "integrity": "sha512-5dgndWOriYSm5cnYaJNhalLNDKOqFwyDB/rr1E9ZsGciGvKPs8R2xYGCacuf3z6K1YKDz182fd+fY3cn3pMqXQ==",
      "dev": true,
      "requires": {
        "graceful-fs": "^4.1.6",
        "universalify": "^2.0.0"
      }
    },
    "jsonparse": {
      "version": "1.3.1",
      "resolved": "https://registry.npmjs.org/jsonparse/-/jsonparse-1.3.1.tgz",
      "integrity": "sha1-P02uSpH6wxX3EGL4UhzCOfE2YoA=",
      "dev": true
    },
    "karma": {
      "version": "6.3.12",
      "resolved": "https://registry.npmjs.org/karma/-/karma-6.3.12.tgz",
      "integrity": "sha512-qwIG+oB2YmHx4hjvYSRMNzL3YWAJ9baHaLAxiP7biFNkfpwYTUTtPck0joFpucalNLzMr+7z/FX1uY/kl8DV9A==",
      "dev": true,
      "requires": {
        "body-parser": "^1.19.0",
        "braces": "^3.0.2",
        "chokidar": "^3.5.1",
        "colors": "1.4.0",
        "connect": "^3.7.0",
        "di": "^0.0.1",
        "dom-serialize": "^2.2.1",
        "glob": "^7.1.7",
        "graceful-fs": "^4.2.6",
        "http-proxy": "^1.18.1",
        "isbinaryfile": "^4.0.8",
        "lodash": "^4.17.21",
        "log4js": "^6.3.0",
        "mime": "^2.5.2",
        "minimatch": "^3.0.4",
        "qjobs": "^1.2.0",
        "range-parser": "^1.2.1",
        "rimraf": "^3.0.2",
        "socket.io": "^4.2.0",
        "source-map": "^0.6.1",
        "tmp": "^0.2.1",
        "ua-parser-js": "^0.7.30",
        "yargs": "^16.1.1"
      },
      "dependencies": {
        "source-map": {
          "version": "0.6.1",
          "resolved": "https://registry.npmjs.org/source-map/-/source-map-0.6.1.tgz",
          "integrity": "sha512-UjgapumWlbMhkBgzT7Ykc5YXUT46F0iKu8SGXq0bcwP5dz/h0Plj6enJqjz1Zbq2l5WaqYnrVbwWOWMyF3F47g==",
          "dev": true
        },
        "tmp": {
          "version": "0.2.1",
          "resolved": "https://registry.npmjs.org/tmp/-/tmp-0.2.1.tgz",
          "integrity": "sha512-76SUhtfqR2Ijn+xllcI5P1oyannHNHByD80W1q447gU3mp9G9PSpGdWmjUOHRDPiHYacIk66W7ubDTuPF3BEtQ==",
          "dev": true,
          "requires": {
            "rimraf": "^3.0.0"
          }
        },
        "yargs": {
          "version": "16.2.0",
          "resolved": "https://registry.npmjs.org/yargs/-/yargs-16.2.0.tgz",
          "integrity": "sha512-D1mvvtDG0L5ft/jGWkLpG1+m0eQxOfaBvTNELraWj22wSVUMWxZUvYgJYcKh6jGGIkJFhH4IZPQhR4TKpc8mBw==",
          "dev": true,
          "requires": {
            "cliui": "^7.0.2",
            "escalade": "^3.1.1",
            "get-caller-file": "^2.0.5",
            "require-directory": "^2.1.1",
            "string-width": "^4.2.0",
            "y18n": "^5.0.5",
            "yargs-parser": "^20.2.2"
          }
        },
        "yargs-parser": {
          "version": "20.2.9",
          "resolved": "https://registry.npmjs.org/yargs-parser/-/yargs-parser-20.2.9.tgz",
          "integrity": "sha512-y11nGElTIV+CT3Zv9t7VKl+Q3hTQoT9a1Qzezhhl6Rp21gJ/IVTW7Z3y9EWXhuUBC2Shnf+DX0antecpAwSP8w==",
          "dev": true
        }
      }
    },
    "karma-chrome-launcher": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/karma-chrome-launcher/-/karma-chrome-launcher-3.1.0.tgz",
      "integrity": "sha512-3dPs/n7vgz1rxxtynpzZTvb9y/GIaW8xjAwcIGttLbycqoFtI7yo1NGnQi6oFTherRE+GIhCAHZC4vEqWGhNvg==",
      "dev": true,
      "requires": {
        "which": "^1.2.1"
      }
    },
    "karma-coverage": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/karma-coverage/-/karma-coverage-2.1.0.tgz",
      "integrity": "sha512-uIejpnArNFQIovB6EPsKO/T4XofELdJWXcA2ADXztFlKhHbr0Ws6ba7wKTMVWsIhEs4iJxdhQkCQrkkhFJSZCw==",
      "dev": true,
      "requires": {
        "istanbul-lib-coverage": "^3.2.0",
        "istanbul-lib-instrument": "^4.0.3",
        "istanbul-lib-report": "^3.0.0",
        "istanbul-lib-source-maps": "^4.0.1",
        "istanbul-reports": "^3.0.5",
        "minimatch": "^3.0.4"
      },
      "dependencies": {
        "istanbul-lib-instrument": {
          "version": "4.0.3",
          "resolved": "https://registry.npmjs.org/istanbul-lib-instrument/-/istanbul-lib-instrument-4.0.3.tgz",
          "integrity": "sha512-BXgQl9kf4WTCPCCpmFGoJkz/+uhvm7h7PFKUYxh7qarQd3ER33vHG//qaE8eN25l07YqZPpHXU9I09l/RD5aGQ==",
          "dev": true,
          "requires": {
            "@babel/core": "^7.7.5",
            "@istanbuljs/schema": "^0.1.2",
            "istanbul-lib-coverage": "^3.0.0",
            "semver": "^6.3.0"
          }
        },
        "semver": {
          "version": "6.3.0",
          "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.0.tgz",
          "integrity": "sha512-b39TBaTSfV6yBrapU89p5fKekE2m/NwnDocOVruQFS1/veMgdzuPcnOM34M6CwxW8jH/lxEa5rBoDeUwu5HHTw==",
          "dev": true
        }
      }
    },
    "karma-jasmine": {
      "version": "4.0.1",
      "resolved": "https://registry.npmjs.org/karma-jasmine/-/karma-jasmine-4.0.1.tgz",
      "integrity": "sha512-h8XDAhTiZjJKzfkoO1laMH+zfNlra+dEQHUAjpn5JV1zCPtOIVWGQjLBrqhnzQa/hrU2XrZwSyBa6XjEBzfXzw==",
      "dev": true,
      "requires": {
        "jasmine-core": "^3.6.0"
      }
    },
    "karma-jasmine-html-reporter": {
      "version": "1.7.0",
      "resolved": "https://registry.npmjs.org/karma-jasmine-html-reporter/-/karma-jasmine-html-reporter-1.7.0.tgz",
      "integrity": "sha512-pzum1TL7j90DTE86eFt48/s12hqwQuiD+e5aXx2Dc9wDEn2LfGq6RoAxEZZjFiN0RDSCOnosEKRZWxbQ+iMpQQ==",
      "dev": true,
      "requires": {}
    },
    "karma-source-map-support": {
      "version": "1.4.0",
      "resolved": "https://registry.npmjs.org/karma-source-map-support/-/karma-source-map-support-1.4.0.tgz",
      "integrity": "sha512-RsBECncGO17KAoJCYXjv+ckIz+Ii9NCi+9enk+rq6XC81ezYkb4/RHE6CTXdA7IOJqoF3wcaLfVG0CPmE5ca6A==",
      "dev": true,
      "requires": {
        "source-map-support": "^0.5.5"
      }
    },
    "keyv": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/keyv/-/keyv-3.1.0.tgz",
      "integrity": "sha512-9ykJ/46SN/9KPM/sichzQ7OvXyGDYKGTaDlKMGCAlg2UK8KRy4jb0d8sFc+0Tt0YYnThq8X2RZgCg74RPxgcVA==",
      "requires": {
        "json-buffer": "3.0.0"
      }
    },
    "kind-of": {
      "version": "6.0.3",
      "resolved": "https://registry.npmjs.org/kind-of/-/kind-of-6.0.3.tgz",
      "integrity": "sha512-dcS1ul+9tmeD95T+x28/ehLgd9mENa3LsvDTtzm3vyBEO7RPptvAD+t44WVXaUjTBRcrpFeFlC8WCruUR456hw==",
      "dev": true
    },
    "klona": {
      "version": "2.0.5",
      "resolved": "https://registry.npmjs.org/klona/-/klona-2.0.5.tgz",
      "integrity": "sha512-pJiBpiXMbt7dkzXe8Ghj/u4FfXOOa98fPW+bihOJ4SjnoijweJrNThJfd3ifXpXhREjpoF2mZVH1GfS9LV3kHQ==",
      "dev": true
    },
    "latest-version": {
      "version": "5.1.0",
      "resolved": "https://registry.npmjs.org/latest-version/-/latest-version-5.1.0.tgz",
      "integrity": "sha512-weT+r0kTkRQdCdYCNtkMwWXQTMEswKrFBkm4ckQOMVhhqhIMI1UT2hMj+1iigIhgSZm5gTmrRXBNoGUgaTY1xA==",
      "requires": {
        "package-json": "^6.3.0"
      }
    },
    "less": {
      "version": "4.1.2",
      "resolved": "https://registry.npmjs.org/less/-/less-4.1.2.tgz",
      "integrity": "sha512-EoQp/Et7OSOVu0aJknJOtlXZsnr8XE8KwuzTHOLeVSEx8pVWUICc8Q0VYRHgzyjX78nMEyC/oztWFbgyhtNfDA==",
      "dev": true,
      "requires": {
        "copy-anything": "^2.0.1",
        "errno": "^0.1.1",
        "graceful-fs": "^4.1.2",
        "image-size": "~0.5.0",
        "make-dir": "^2.1.0",
        "mime": "^1.4.1",
        "needle": "^2.5.2",
        "parse-node-version": "^1.0.1",
        "source-map": "~0.6.0",
        "tslib": "^2.3.0"
      },
      "dependencies": {
        "make-dir": {
          "version": "2.1.0",
          "resolved": "https://registry.npmjs.org/make-dir/-/make-dir-2.1.0.tgz",
          "integrity": "sha512-LS9X+dc8KLxXCb8dni79fLIIUA5VyZoyjSMCwTluaXA0o27cCK0bhXkpgw+sTXVpPy/lSO57ilRixqk0vDmtRA==",
          "dev": true,
          "optional": true,
          "requires": {
            "pify": "^4.0.1",
            "semver": "^5.6.0"
          }
        },
        "mime": {
          "version": "1.6.0",
          "resolved": "https://registry.npmjs.org/mime/-/mime-1.6.0.tgz",
          "integrity": "sha512-x0Vn8spI+wuJ1O6S7gnbaQg8Pxh4NNHb7KSINmEWKiPE4RKOplvijn+NkmYmmRgP68mc70j2EbeTFRsrswaQeg==",
          "dev": true,
          "optional": true
        },
        "pify": {
          "version": "4.0.1",
          "resolved": "https://registry.npmjs.org/pify/-/pify-4.0.1.tgz",
          "integrity": "sha512-uB80kBFb/tfd68bVleG9T5GGsGPjJrLAUpR5PZIrhBnIaRTQRjqdJSsIKkOP6OAIFbj7GOrcudc5pNjZ+geV2g==",
          "dev": true,
          "optional": true
        },
        "semver": {
          "version": "5.7.1",
          "resolved": "https://registry.npmjs.org/semver/-/semver-5.7.1.tgz",
          "integrity": "sha512-sauaDf/PZdVgrLTNYHRtpXa1iRiKcaebiKQ1BJdpQlWH2lCvexQdX55snPFyK7QzpudqbCI0qXFfOasHdyNDGQ==",
          "dev": true,
          "optional": true
        },
        "source-map": {
          "version": "0.6.1",
          "resolved": "https://registry.npmjs.org/source-map/-/source-map-0.6.1.tgz",
          "integrity": "sha512-UjgapumWlbMhkBgzT7Ykc5YXUT46F0iKu8SGXq0bcwP5dz/h0Plj6enJqjz1Zbq2l5WaqYnrVbwWOWMyF3F47g==",
          "dev": true,
          "optional": true
        }
      }
    },
    "less-loader": {
      "version": "10.2.0",
      "resolved": "https://registry.npmjs.org/less-loader/-/less-loader-10.2.0.tgz",
      "integrity": "sha512-AV5KHWvCezW27GT90WATaDnfXBv99llDbtaj4bshq6DvAihMdNjaPDcUMa6EXKLRF+P2opFenJp89BXg91XLYg==",
      "dev": true,
      "requires": {
        "klona": "^2.0.4"
      }
    },
    "license-webpack-plugin": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/license-webpack-plugin/-/license-webpack-plugin-4.0.0.tgz",
      "integrity": "sha512-b9iMrROrw2fTOJBZ57h0xJfT5/1Cxg4ucYbtpWoukv4Awb2TFPfDDFVHNM8w6SYQpVfB13a5tQJxgGamqwrsyw==",
      "dev": true,
      "requires": {
        "webpack-sources": "^3.0.0"
      }
    },
    "lines-and-columns": {
      "version": "1.2.4",
      "resolved": "https://registry.npmjs.org/lines-and-columns/-/lines-and-columns-1.2.4.tgz",
      "integrity": "sha512-7ylylesZQ/PV29jhEDl3Ufjo6ZX7gCqJr5F7PKrqc93v7fzSymt1BpwEU8nAUXs8qzzvqhbjhK5QZg6Mt/HkBg==",
      "dev": true
    },
    "loader-runner": {
      "version": "4.2.0",
      "resolved": "https://registry.npmjs.org/loader-runner/-/loader-runner-4.2.0.tgz",
      "integrity": "sha512-92+huvxMvYlMzMt0iIOukcwYBFpkYJdpl2xsZ7LrlayO7E8SOv+JJUEK17B/dJIHAOLMfh2dZZ/Y18WgmGtYNw==",
      "dev": true
    },
    "loader-utils": {
      "version": "3.2.0",
      "resolved": "https://registry.npmjs.org/loader-utils/-/loader-utils-3.2.0.tgz",
      "integrity": "sha512-HVl9ZqccQihZ7JM85dco1MvO9G+ONvxoGa9rkhzFsneGLKSUg1gJf9bWzhRhcvm2qChhWpebQhP44qxjKIUCaQ==",
      "dev": true
    },
    "locate-path": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/locate-path/-/locate-path-5.0.0.tgz",
      "integrity": "sha512-t7hw9pI+WvuwNJXwk5zVHpyhIqzg2qTlklJOf0mVxGSbe3Fp2VieZcduNYjaLDoy6p9uGpQEGWG87WpMKlNq8g==",
      "dev": true,
      "requires": {
        "p-locate": "^4.1.0"
      }
    },
    "lodash": {
      "version": "4.17.21",
      "resolved": "https://registry.npmjs.org/lodash/-/lodash-4.17.21.tgz",
      "integrity": "sha512-v2kDEe57lecTulaDIuNTPy3Ry4gLGJ6Z1O3vE1krgXZNrsQ+LFTGHVxVjcXPs17LhbZVGedAJv8XZ1tvj5FvSg=="
    },
    "lodash-id": {
      "version": "0.14.1",
      "resolved": "https://registry.npmjs.org/lodash-id/-/lodash-id-0.14.1.tgz",
      "integrity": "sha512-ikQPBTiq/d5m6dfKQlFdIXFzvThPi2Be9/AHxktOnDSfSxE1j9ICbBT5Elk1ke7HSTgM38LHTpmJovo9/klnLg=="
    },
    "lodash.debounce": {
      "version": "4.0.8",
      "resolved": "https://registry.npmjs.org/lodash.debounce/-/lodash.debounce-4.0.8.tgz",
      "integrity": "sha1-gteb/zCmfEAF/9XiUVMArZyk168=",
      "dev": true
    },
    "log-symbols": {
      "version": "4.1.0",
      "resolved": "https://registry.npmjs.org/log-symbols/-/log-symbols-4.1.0.tgz",
      "integrity": "sha512-8XPvpAA8uyhfteu8pIvQxpJZ7SYYdpUivZpGy6sFsBuKRY/7rQGavedeB8aK+Zkyq6upMFVL/9AW6vOYzfRyLg==",
      "dev": true,
      "requires": {
        "chalk": "^4.1.0",
        "is-unicode-supported": "^0.1.0"
      },
      "dependencies": {
        "ansi-styles": {
          "version": "4.3.0",
          "resolved": "https://registry.npmjs.org/ansi-styles/-/ansi-styles-4.3.0.tgz",
          "integrity": "sha512-zbB9rCJAT1rbjiVDb2hqKFHNYLxgtk8NURxZ3IZwD3F6NtxbXZQCnnSi1Lkx+IDohdPlFp222wVALIheZJQSEg==",
          "dev": true,
          "requires": {
            "color-convert": "^2.0.1"
          }
        },
        "chalk": {
          "version": "4.1.2",
          "resolved": "https://registry.npmjs.org/chalk/-/chalk-4.1.2.tgz",
          "integrity": "sha512-oKnbhFyRIXpUuez8iBMmyEa4nbj4IOQyuhc/wy9kY7/WVPcwIO9VA668Pu8RkO7+0G76SLROeyw9CpQ061i4mA==",
          "dev": true,
          "requires": {
            "ansi-styles": "^4.1.0",
            "supports-color": "^7.1.0"
          }
        },
        "color-convert": {
          "version": "2.0.1",
          "resolved": "https://registry.npmjs.org/color-convert/-/color-convert-2.0.1.tgz",
          "integrity": "sha512-RRECPsj7iu/xb5oKYcsFHSppFNnsj/52OVTRKb4zP5onXwVF3zVmmToNcOfGC+CRDpfK/U584fMg38ZHCaElKQ==",
          "dev": true,
          "requires": {
            "color-name": "~1.1.4"
          }
        },
        "color-name": {
          "version": "1.1.4",
          "resolved": "https://registry.npmjs.org/color-name/-/color-name-1.1.4.tgz",
          "integrity": "sha512-dOy+3AuW3a2wNbZHIuMZpTcgjGuLU/uBL/ubcZF9OXbDo8ff4O8yVp5Bf0efS8uEoYo5q4Fx7dY9OgQGXgAsQA==",
          "dev": true
        },
        "has-flag": {
          "version": "4.0.0",
          "resolved": "https://registry.npmjs.org/has-flag/-/has-flag-4.0.0.tgz",
          "integrity": "sha512-EykJT/Q1KjTWctppgIAgfSO0tKVuZUjhgMr17kqTumMl6Afv3EISleU7qZUzoXDFTAHTDC4NOoG/ZxU3EvlMPQ==",
          "dev": true
        },
        "supports-color": {
          "version": "7.2.0",
          "resolved": "https://registry.npmjs.org/supports-color/-/supports-color-7.2.0.tgz",
          "integrity": "sha512-qpCAvRl9stuOHveKsn7HncJRvv501qIacKzQlO/+Lwxc9+0q2wLyv4Dfvt80/DPn2pqOBsJdDiogXGR9+OvwRw==",
          "dev": true,
          "requires": {
            "has-flag": "^4.0.0"
          }
        }
      }
    },
    "log4js": {
      "version": "6.4.1",
      "resolved": "https://registry.npmjs.org/log4js/-/log4js-6.4.1.tgz",
      "integrity": "sha512-iUiYnXqAmNKiIZ1XSAitQ4TmNs8CdZYTAWINARF3LjnsLN8tY5m0vRwd6uuWj/yNY0YHxeZodnbmxKFUOM2rMg==",
      "dev": true,
      "requires": {
        "date-format": "^4.0.3",
        "debug": "^4.3.3",
        "flatted": "^3.2.4",
        "rfdc": "^1.3.0",
        "streamroller": "^3.0.2"
      }
    },
    "lowdb": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/lowdb/-/lowdb-1.0.0.tgz",
      "integrity": "sha512-2+x8esE/Wb9SQ1F9IHaYWfsC9FIecLOPrK4g17FGEayjUWH172H6nwicRovGvSE2CPZouc2MCIqCI7h9d+GftQ==",
      "requires": {
        "graceful-fs": "^4.1.3",
        "is-promise": "^2.1.0",
        "lodash": "4",
        "pify": "^3.0.0",
        "steno": "^0.4.1"
      },
      "dependencies": {
        "pify": {
          "version": "3.0.0",
          "resolved": "https://registry.npmjs.org/pify/-/pify-3.0.0.tgz",
          "integrity": "sha1-5aSs0sEB/fPZpNB/DbxNtJ3SgXY="
        }
      }
    },
    "lowercase-keys": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/lowercase-keys/-/lowercase-keys-1.0.1.tgz",
      "integrity": "sha512-G2Lj61tXDnVFFOi8VZds+SoQjtQC3dgokKdDG2mTm1tx4m50NUHBOZSBwQQHyy0V12A0JTG4icfZQH+xPyh8VA=="
    },
    "lru-cache": {
      "version": "6.0.0",
      "resolved": "https://registry.npmjs.org/lru-cache/-/lru-cache-6.0.0.tgz",
      "integrity": "sha512-Jo6dJ04CmSjuznwJSS3pUeWmd/H0ffTlkXXgwZi+eq1UCmqQwCh+eLsYOYCwY991i2Fah4h1BEMCx4qThGbsiA==",
      "requires": {
        "yallist": "^4.0.0"
      }
    },
    "magic-string": {
      "version": "0.25.7",
      "resolved": "https://registry.npmjs.org/magic-string/-/magic-string-0.25.7.tgz",
      "integrity": "sha512-4CrMT5DOHTDk4HYDlzmwu4FVCcIYI8gauveasrdCu2IKIFOJ3f0v/8MDGJCDL9oD2ppz/Av1b0Nj345H9M+XIA==",
      "dev": true,
      "requires": {
        "sourcemap-codec": "^1.4.4"
      }
    },
    "make-dir": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/make-dir/-/make-dir-3.1.0.tgz",
      "integrity": "sha512-g3FeP20LNwhALb/6Cz6Dd4F2ngze0jz7tbzrD2wAV+o9FeNHe4rL+yK2md0J/fiSf1sa1ADhXqi5+oVwOM/eGw==",
      "requires": {
        "semver": "^6.0.0"
      },
      "dependencies": {
        "semver": {
          "version": "6.3.0",
          "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.0.tgz",
          "integrity": "sha512-b39TBaTSfV6yBrapU89p5fKekE2m/NwnDocOVruQFS1/veMgdzuPcnOM34M6CwxW8jH/lxEa5rBoDeUwu5HHTw=="
        }
      }
    },
    "make-fetch-happen": {
      "version": "9.1.0",
      "resolved": "https://registry.npmjs.org/make-fetch-happen/-/make-fetch-happen-9.1.0.tgz",
      "integrity": "sha512-+zopwDy7DNknmwPQplem5lAZX/eCOzSvSNNcSKm5eVwTkOBzoktEfXsa9L23J/GIRhxRsaxzkPEhrJEpE2F4Gg==",
      "dev": true,
      "requires": {
        "agentkeepalive": "^4.1.3",
        "cacache": "^15.2.0",
        "http-cache-semantics": "^4.1.0",
        "http-proxy-agent": "^4.0.1",
        "https-proxy-agent": "^5.0.0",
        "is-lambda": "^1.0.1",
        "lru-cache": "^6.0.0",
        "minipass": "^3.1.3",
        "minipass-collect": "^1.0.2",
        "minipass-fetch": "^1.3.2",
        "minipass-flush": "^1.0.5",
        "minipass-pipeline": "^1.2.4",
        "negotiator": "^0.6.2",
        "promise-retry": "^2.0.1",
        "socks-proxy-agent": "^6.0.0",
        "ssri": "^8.0.0"
      }
    },
    "media-typer": {
      "version": "0.3.0",
      "resolved": "https://registry.npmjs.org/media-typer/-/media-typer-0.3.0.tgz",
      "integrity": "sha1-hxDXrwqmJvj/+hzgAWhUUmMlV0g="
    },
    "memfs": {
      "version": "3.4.1",
      "resolved": "https://registry.npmjs.org/memfs/-/memfs-3.4.1.tgz",
      "integrity": "sha512-1c9VPVvW5P7I85c35zAdEr1TD5+F11IToIHIlrVIcflfnzPkJa0ZoYEoEdYDP8KgPFoSZ/opDrUsAoZWym3mtw==",
      "dev": true,
      "requires": {
        "fs-monkey": "1.0.3"
      }
    },
    "merge-descriptors": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/merge-descriptors/-/merge-descriptors-1.0.1.tgz",
      "integrity": "sha1-sAqqVW3YtEVoFQ7J0blT8/kMu2E="
    },
    "merge-stream": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/merge-stream/-/merge-stream-2.0.0.tgz",
      "integrity": "sha512-abv/qOcuPfk3URPfDzmZU1LKmuw8kT+0nIHvKrKgFrwifol/doWcdA4ZqsWQ8ENrFKkd67Mfpo/LovbIUsbt3w==",
      "dev": true
    },
    "merge2": {
      "version": "1.4.1",
      "resolved": "https://registry.npmjs.org/merge2/-/merge2-1.4.1.tgz",
      "integrity": "sha512-8q7VEgMJW4J8tcfVPy8g09NcQwZdbwFEqhe/WZkoIzjn/3TGDwtOCYtXGxA3O8tPzpczCCDgv+P2P5y00ZJOOg==",
      "dev": true
    },
    "method-override": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/method-override/-/method-override-3.0.0.tgz",
      "integrity": "sha512-IJ2NNN/mSl9w3kzWB92rcdHpz+HjkxhDJWNDBqSlas+zQdP8wBiJzITPg08M/k2uVvMow7Sk41atndNtt/PHSA==",
      "requires": {
        "debug": "3.1.0",
        "methods": "~1.1.2",
        "parseurl": "~1.3.2",
        "vary": "~1.1.2"
      },
      "dependencies": {
        "debug": {
          "version": "3.1.0",
          "resolved": "https://registry.npmjs.org/debug/-/debug-3.1.0.tgz",
          "integrity": "sha512-OX8XqP7/1a9cqkxYw2yXss15f26NKWBpDXQd0/uK/KPqdQhxbPa994hnzjcE2VqQpDslf55723cKPUOGSmMY3g==",
          "requires": {
            "ms": "2.0.0"
          }
        },
        "ms": {
          "version": "2.0.0",
          "resolved": "https://registry.npmjs.org/ms/-/ms-2.0.0.tgz",
          "integrity": "sha1-VgiurfwAvmwpAd9fmGF4jeDVl8g="
        }
      }
    },
    "methods": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/methods/-/methods-1.1.2.tgz",
      "integrity": "sha1-VSmk1nZUE07cxSZmVoNbD4Ua/O4="
    },
    "micromatch": {
      "version": "4.0.4",
      "resolved": "https://registry.npmjs.org/micromatch/-/micromatch-4.0.4.tgz",
      "integrity": "sha512-pRmzw/XUcwXGpD9aI9q/0XOwLNygjETJ8y0ao0wdqprrzDa4YnxLcz7fQRZr8voh8V10kGhABbNcHVk5wHgWwg==",
      "dev": true,
      "requires": {
        "braces": "^3.0.1",
        "picomatch": "^2.2.3"
      }
    },
    "mime": {
      "version": "2.6.0",
      "resolved": "https://registry.npmjs.org/mime/-/mime-2.6.0.tgz",
      "integrity": "sha512-USPkMeET31rOMiarsBNIHZKLGgvKc/LrjofAnBlOttf5ajRvqiRA8QsenbcooctK6d6Ts6aqZXBA+XbkKthiQg==",
      "dev": true
    },
    "mime-db": {
      "version": "1.51.0",
      "resolved": "https://registry.npmjs.org/mime-db/-/mime-db-1.51.0.tgz",
      "integrity": "sha512-5y8A56jg7XVQx2mbv1lu49NR4dokRnhZYTtL+KGfaa27uq4pSTXkwQkFJl4pkRMyNFz/EtYDSkiiEHx3F7UN6g=="
    },
    "mime-types": {
      "version": "2.1.34",
      "resolved": "https://registry.npmjs.org/mime-types/-/mime-types-2.1.34.tgz",
      "integrity": "sha512-6cP692WwGIs9XXdOO4++N+7qjqv0rqxxVvJ3VHPh/Sc9mVZcQP+ZGhkKiTvWMQRr2tbHkJP/Yn7Y0npb3ZBs4A==",
      "requires": {
        "mime-db": "1.51.0"
      }
    },
    "mimic-fn": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/mimic-fn/-/mimic-fn-2.1.0.tgz",
      "integrity": "sha512-OqbOk5oEQeAZ8WXWydlu9HJjz9WVdEIvamMCcXmuqUYjTknH/sqsWvhQ3vgwKFRR1HpjvNBKQ37nbJgYzGqGcg==",
      "dev": true
    },
    "mimic-response": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/mimic-response/-/mimic-response-1.0.1.tgz",
      "integrity": "sha512-j5EctnkH7amfV/q5Hgmoal1g2QHFJRraOtmx0JpIqkxhBhI/lJSl1nMpQ45hVarwNETOoWEimndZ4QK0RHxuxQ=="
    },
    "mini-css-extract-plugin": {
      "version": "2.4.5",
      "resolved": "https://registry.npmjs.org/mini-css-extract-plugin/-/mini-css-extract-plugin-2.4.5.tgz",
      "integrity": "sha512-oEIhRucyn1JbT/1tU2BhnwO6ft1jjH1iCX9Gc59WFMg0n5773rQU0oyQ0zzeYFFuBfONaRbQJyGoPtuNseMxjA==",
      "dev": true,
      "requires": {
        "schema-utils": "^4.0.0"
      },
      "dependencies": {
        "schema-utils": {
          "version": "4.0.0",
          "resolved": "https://registry.npmjs.org/schema-utils/-/schema-utils-4.0.0.tgz",
          "integrity": "sha512-1edyXKgh6XnJsJSQ8mKWXnN/BVaIbFMLpouRUrXgVq7WYne5kw3MW7UPhO44uRXQSIpTSXoJbmrR2X0w9kUTyg==",
          "dev": true,
          "requires": {
            "@types/json-schema": "^7.0.9",
            "ajv": "^8.8.0",
            "ajv-formats": "^2.1.1",
            "ajv-keywords": "^5.0.0"
          }
        }
      }
    },
    "minimalistic-assert": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/minimalistic-assert/-/minimalistic-assert-1.0.1.tgz",
      "integrity": "sha512-UtJcAD4yEaGtjPezWuO9wC4nwUnVH/8/Im3yEHQP4b67cXlD/Qr9hdITCU1xDbSEXg2XKNaP8jsReV7vQd00/A==",
      "dev": true
    },
    "minimatch": {
      "version": "3.0.4",
      "resolved": "https://registry.npmjs.org/minimatch/-/minimatch-3.0.4.tgz",
      "integrity": "sha512-yJHVQEhyqPLUTgt9B83PXu6W3rx4MvvHvSUvToogpwoGDOUQ+yDrR0HRot+yOCdCO7u4hX3pWft6kWBBcqh0UA==",
      "dev": true,
      "requires": {
        "brace-expansion": "^1.1.7"
      }
    },
    "minimist": {
      "version": "1.2.5",
      "resolved": "https://registry.npmjs.org/minimist/-/minimist-1.2.5.tgz",
      "integrity": "sha512-FM9nNUYrRBAELZQT3xeZQ7fmMOBg6nWNmJKTcgsJeaLstP/UODVpGsr5OhXhhXg6f+qtJ8uiZ+PUxkDWcgIXLw=="
    },
    "minipass": {
      "version": "3.1.6",
      "resolved": "https://registry.npmjs.org/minipass/-/minipass-3.1.6.tgz",
      "integrity": "sha512-rty5kpw9/z8SX9dmxblFA6edItUmwJgMeYDZRrwlIVN27i8gysGbznJwUggw2V/FVqFSDdWy040ZPS811DYAqQ==",
      "dev": true,
      "requires": {
        "yallist": "^4.0.0"
      }
    },
    "minipass-collect": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/minipass-collect/-/minipass-collect-1.0.2.tgz",
      "integrity": "sha512-6T6lH0H8OG9kITm/Jm6tdooIbogG9e0tLgpY6mphXSm/A9u8Nq1ryBG+Qspiub9LjWlBPsPS3tWQ/Botq4FdxA==",
      "dev": true,
      "requires": {
        "minipass": "^3.0.0"
      }
    },
    "minipass-fetch": {
      "version": "1.4.1",
      "resolved": "https://registry.npmjs.org/minipass-fetch/-/minipass-fetch-1.4.1.tgz",
      "integrity": "sha512-CGH1eblLq26Y15+Azk7ey4xh0J/XfJfrCox5LDJiKqI2Q2iwOLOKrlmIaODiSQS8d18jalF6y2K2ePUm0CmShw==",
      "dev": true,
      "requires": {
        "encoding": "^0.1.12",
        "minipass": "^3.1.0",
        "minipass-sized": "^1.0.3",
        "minizlib": "^2.0.0"
      }
    },
    "minipass-flush": {
      "version": "1.0.5",
      "resolved": "https://registry.npmjs.org/minipass-flush/-/minipass-flush-1.0.5.tgz",
      "integrity": "sha512-JmQSYYpPUqX5Jyn1mXaRwOda1uQ8HP5KAT/oDSLCzt1BYRhQU0/hDtsB1ufZfEEzMZ9aAVmsBw8+FWsIXlClWw==",
      "dev": true,
      "requires": {
        "minipass": "^3.0.0"
      }
    },
    "minipass-json-stream": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/minipass-json-stream/-/minipass-json-stream-1.0.1.tgz",
      "integrity": "sha512-ODqY18UZt/I8k+b7rl2AENgbWE8IDYam+undIJONvigAz8KR5GWblsFTEfQs0WODsjbSXWlm+JHEv8Gr6Tfdbg==",
      "dev": true,
      "requires": {
        "jsonparse": "^1.3.1",
        "minipass": "^3.0.0"
      }
    },
    "minipass-pipeline": {
      "version": "1.2.4",
      "resolved": "https://registry.npmjs.org/minipass-pipeline/-/minipass-pipeline-1.2.4.tgz",
      "integrity": "sha512-xuIq7cIOt09RPRJ19gdi4b+RiNvDFYe5JH+ggNvBqGqpQXcru3PcRmOZuHBKWK1Txf9+cQ+HMVN4d6z46LZP7A==",
      "dev": true,
      "requires": {
        "minipass": "^3.0.0"
      }
    },
    "minipass-sized": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/minipass-sized/-/minipass-sized-1.0.3.tgz",
      "integrity": "sha512-MbkQQ2CTiBMlA2Dm/5cY+9SWFEN8pzzOXi6rlM5Xxq0Yqbda5ZQy9sU75a673FE9ZK0Zsbr6Y5iP6u9nktfg2g==",
      "dev": true,
      "requires": {
        "minipass": "^3.0.0"
      }
    },
    "minizlib": {
      "version": "2.1.2",
      "resolved": "https://registry.npmjs.org/minizlib/-/minizlib-2.1.2.tgz",
      "integrity": "sha512-bAxsR8BVfj60DWXHE3u30oHzfl4G7khkSuPW+qvpd7jFRHm7dLxOjUk1EHACJ/hxLY8phGJ0YhYHZo7jil7Qdg==",
      "dev": true,
      "requires": {
        "minipass": "^3.0.0",
        "yallist": "^4.0.0"
      }
    },
    "mkdirp": {
      "version": "1.0.4",
      "resolved": "https://registry.npmjs.org/mkdirp/-/mkdirp-1.0.4.tgz",
      "integrity": "sha512-vVqVZQyf3WLx2Shd0qJ9xuvqgAyKPLAiqITEtqW0oIUjzo3PePDd6fW9iFz30ef7Ysp/oiWqbhszeGWW2T6Gzw==",
      "dev": true
    },
    "morgan": {
      "version": "1.10.0",
      "resolved": "https://registry.npmjs.org/morgan/-/morgan-1.10.0.tgz",
      "integrity": "sha512-AbegBVI4sh6El+1gNwvD5YIck7nSA36weD7xvIxG4in80j/UoK8AEGaWnnz8v1GxonMCltmlNs5ZKbGvl9b1XQ==",
      "requires": {
        "basic-auth": "~2.0.1",
        "debug": "2.6.9",
        "depd": "~2.0.0",
        "on-finished": "~2.3.0",
        "on-headers": "~1.0.2"
      },
      "dependencies": {
        "debug": {
          "version": "2.6.9",
          "resolved": "https://registry.npmjs.org/debug/-/debug-2.6.9.tgz",
          "integrity": "sha512-bC7ElrdJaJnPbAP+1EotYvqZsb3ecl5wi6Bfi6BJTUcNowp6cvspg0jXznRTKDjm/E7AdgFBVeAPVMNcKGsHMA==",
          "requires": {
            "ms": "2.0.0"
          }
        },
        "depd": {
          "version": "2.0.0",
          "resolved": "https://registry.npmjs.org/depd/-/depd-2.0.0.tgz",
          "integrity": "sha512-g7nH6P6dyDioJogAAGprGpCtVImJhpPk/roCzdb3fIh61/s/nPsfR6onyMwkCAR/OlC3yBC0lESvUoQEAssIrw=="
        },
        "ms": {
          "version": "2.0.0",
          "resolved": "https://registry.npmjs.org/ms/-/ms-2.0.0.tgz",
          "integrity": "sha1-VgiurfwAvmwpAd9fmGF4jeDVl8g="
        }
      }
    },
    "ms": {
      "version": "2.1.2",
      "resolved": "https://registry.npmjs.org/ms/-/ms-2.1.2.tgz",
      "integrity": "sha512-sGkPx+VjMtmA6MX27oA4FBFELFCZZ4S4XqeGOXCv68tT+jb3vk/RyaKWP0PTKyWtmLSM0b+adUTEvbs1PEaH2w=="
    },
    "multicast-dns": {
      "version": "6.2.3",
      "resolved": "https://registry.npmjs.org/multicast-dns/-/multicast-dns-6.2.3.tgz",
      "integrity": "sha512-ji6J5enbMyGRHIAkAOu3WdV8nggqviKCEKtXcOqfphZZtQrmHKycfynJ2V7eVPUA4NhJ6V7Wf4TmGbTwKE9B6g==",
      "dev": true,
      "requires": {
        "dns-packet": "^1.3.1",
        "thunky": "^1.0.2"
      }
    },
    "multicast-dns-service-types": {
      "version": "1.1.0",
      "resolved": "https://registry.npmjs.org/multicast-dns-service-types/-/multicast-dns-service-types-1.1.0.tgz",
      "integrity": "sha1-iZ8R2WhuXgXLkbNdXw5jt3PPyQE=",
      "dev": true
    },
    "mute-stream": {
      "version": "0.0.8",
      "resolved": "https://registry.npmjs.org/mute-stream/-/mute-stream-0.0.8.tgz",
      "integrity": "sha512-nnbWWOkoWyUsTjKrhgD0dcz22mdkSnpYqbEjIm2nhwhuxlSkpywJmBo8h0ZqJdkp73mb90SssHkN4rsRaBAfAA==",
      "dev": true
    },
    "nanoid": {
      "version": "3.2.0",
      "resolved": "https://registry.npmjs.org/nanoid/-/nanoid-3.2.0.tgz",
      "integrity": "sha512-fmsZYa9lpn69Ad5eDn7FMcnnSR+8R34W9qJEijxYhTbfOWzr22n1QxCMzXLK+ODyW2973V3Fux959iQoUxzUIA=="
    },
    "needle": {
      "version": "2.9.1",
      "resolved": "https://registry.npmjs.org/needle/-/needle-2.9.1.tgz",
      "integrity": "sha512-6R9fqJ5Zcmf+uYaFgdIHmLwNldn5HbK8L5ybn7Uz+ylX/rnOsSp1AHcvQSrCaFN+qNM1wpymHqD7mVasEOlHGQ==",
      "dev": true,
      "optional": true,
      "requires": {
        "debug": "^3.2.6",
        "iconv-lite": "^0.4.4",
        "sax": "^1.2.4"
      },
      "dependencies": {
        "debug": {
          "version": "3.2.7",
          "resolved": "https://registry.npmjs.org/debug/-/debug-3.2.7.tgz",
          "integrity": "sha512-CFjzYYAi4ThfiQvizrFQevTTXHtnCqWfe7x1AhgEscTz6ZbLbfoLRLPugTQyBth6f8ZERVUSyWHFD/7Wu4t1XQ==",
          "dev": true,
          "optional": true,
          "requires": {
            "ms": "^2.1.1"
          }
        }
      }
    },
    "negotiator": {
      "version": "0.6.3",
      "resolved": "https://registry.npmjs.org/negotiator/-/negotiator-0.6.3.tgz",
      "integrity": "sha512-+EUsqGPLsM+j/zdChZjsnX51g4XrHFOIXwfnCVPGlQk/k5giakcKsuxCObBRu6DSm9opw/O6slWbJdghQM4bBg==",
      "dev": true
    },
    "neo-async": {
      "version": "2.6.2",
      "resolved": "https://registry.npmjs.org/neo-async/-/neo-async-2.6.2.tgz",
      "integrity": "sha512-Yd3UES5mWCSqR+qNT93S3UoYUkqAZ9lLg8a7g9rimsWmYGK8cVToA4/sF3RrshdyV3sAGMXVUmpMYOw+dLpOuw==",
      "dev": true
    },
    "nice-napi": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/nice-napi/-/nice-napi-1.0.2.tgz",
      "integrity": "sha512-px/KnJAJZf5RuBGcfD+Sp2pAKq0ytz8j+1NehvgIGFkvtvFrDM3T8E4x/JJODXK9WZow8RRGrbA9QQ3hs+pDhA==",
      "dev": true,
      "optional": true,
      "requires": {
        "node-addon-api": "^3.0.0",
        "node-gyp-build": "^4.2.2"
      }
    },
    "node-addon-api": {
      "version": "3.2.1",
      "resolved": "https://registry.npmjs.org/node-addon-api/-/node-addon-api-3.2.1.tgz",
      "integrity": "sha512-mmcei9JghVNDYydghQmeDX8KoAm0FAiYyIcUt/N4nhyAipB17pllZQDOJD2fotxABnt4Mdz+dKTO7eftLg4d0A==",
      "dev": true,
      "optional": true
    },
    "node-forge": {
      "version": "0.10.0",
      "resolved": "https://registry.npmjs.org/node-forge/-/node-forge-0.10.0.tgz",
      "integrity": "sha512-PPmu8eEeG9saEUvI97fm4OYxXVB6bFvyNTyiUOBichBpFG8A1Ljw3bY62+5oOjDEMHRnd0Y7HQ+x7uzxOzC6JA==",
      "dev": true
    },
    "node-gyp": {
      "version": "8.4.1",
      "resolved": "https://registry.npmjs.org/node-gyp/-/node-gyp-8.4.1.tgz",
      "integrity": "sha512-olTJRgUtAb/hOXG0E93wZDs5YiJlgbXxTwQAFHyNlRsXQnYzUaF2aGgujZbw+hR8aF4ZG/rST57bWMWD16jr9w==",
      "dev": true,
      "requires": {
        "env-paths": "^2.2.0",
        "glob": "^7.1.4",
        "graceful-fs": "^4.2.6",
        "make-fetch-happen": "^9.1.0",
        "nopt": "^5.0.0",
        "npmlog": "^6.0.0",
        "rimraf": "^3.0.2",
        "semver": "^7.3.5",
        "tar": "^6.1.2",
        "which": "^2.0.2"
      },
      "dependencies": {
        "which": {
          "version": "2.0.2",
          "resolved": "https://registry.npmjs.org/which/-/which-2.0.2.tgz",
          "integrity": "sha512-BLI3Tl1TW3Pvl70l3yq3Y64i+awpwXqsGBYWkkqMtnbXgrMD+yj7rhW0kuEDxzJaYXGjEW5ogapKNMEKNMjibA==",
          "dev": true,
          "requires": {
            "isexe": "^2.0.0"
          }
        }
      }
    },
    "node-gyp-build": {
      "version": "4.3.0",
      "resolved": "https://registry.npmjs.org/node-gyp-build/-/node-gyp-build-4.3.0.tgz",
      "integrity": "sha512-iWjXZvmboq0ja1pUGULQBexmxq8CV4xBhX7VDOTbL7ZR4FOowwY/VOtRxBN/yKxmdGoIp4j5ysNT4u3S2pDQ3Q==",
      "dev": true,
      "optional": true
    },
    "node-releases": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/node-releases/-/node-releases-2.0.1.tgz",
      "integrity": "sha512-CqyzN6z7Q6aMeF/ktcMVTzhAHCEpf8SOarwpzpf8pNBY2k5/oM34UHldUwp8VKI7uxct2HxSRdJjBaZeESzcxA==",
      "dev": true
    },
    "nopt": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/nopt/-/nopt-5.0.0.tgz",
      "integrity": "sha512-Tbj67rffqceeLpcRXrT7vKAN8CwfPeIBgM7E6iBkmKLV7bEMwpGgYLGv0jACUsECaa/vuxP0IjEont6umdMgtQ==",
      "dev": true,
      "requires": {
        "abbrev": "1"
      }
    },
    "normalize-path": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/normalize-path/-/normalize-path-3.0.0.tgz",
      "integrity": "sha512-6eZs5Ls3WtCisHWp9S2GUy8dqkpGi4BVSz3GaqiE6ezub0512ESztXUwUB6C6IKbQkY2Pnb/mD4WYojCRwcwLA==",
      "dev": true
    },
    "normalize-range": {
      "version": "0.1.2",
      "resolved": "https://registry.npmjs.org/normalize-range/-/normalize-range-0.1.2.tgz",
      "integrity": "sha1-LRDAa9/TEuqXd2laTShDlFa3WUI=",
      "dev": true
    },
    "normalize-url": {
      "version": "4.5.1",
      "resolved": "https://registry.npmjs.org/normalize-url/-/normalize-url-4.5.1.tgz",
      "integrity": "sha512-9UZCFRHQdNrfTpGg8+1INIg93B6zE0aXMVFkw1WFwvO4SlZywU6aLg5Of0Ap/PgcbSw4LNxvMWXMeugwMCX0AA=="
    },
    "npm-bundled": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/npm-bundled/-/npm-bundled-1.1.2.tgz",
      "integrity": "sha512-x5DHup0SuyQcmL3s7Rx/YQ8sbw/Hzg0rj48eN0dV7hf5cmQq5PXIeioroH3raV1QC1yh3uTYuMThvEQF3iKgGQ==",
      "dev": true,
      "requires": {
        "npm-normalize-package-bin": "^1.0.1"
      }
    },
    "npm-install-checks": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/npm-install-checks/-/npm-install-checks-4.0.0.tgz",
      "integrity": "sha512-09OmyDkNLYwqKPOnbI8exiOZU2GVVmQp7tgez2BPi5OZC8M82elDAps7sxC4l//uSUtotWqoEIDwjRvWH4qz8w==",
      "dev": true,
      "requires": {
        "semver": "^7.1.1"
      }
    },
    "npm-normalize-package-bin": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/npm-normalize-package-bin/-/npm-normalize-package-bin-1.0.1.tgz",
      "integrity": "sha512-EPfafl6JL5/rU+ot6P3gRSCpPDW5VmIzX959Ob1+ySFUuuYHWHekXpwdUZcKP5C+DS4GEtdJluwBjnsNDl+fSA==",
      "dev": true
    },
    "npm-package-arg": {
      "version": "8.1.5",
      "resolved": "https://registry.npmjs.org/npm-package-arg/-/npm-package-arg-8.1.5.tgz",
      "integrity": "sha512-LhgZrg0n0VgvzVdSm1oiZworPbTxYHUJCgtsJW8mGvlDpxTM1vSJc3m5QZeUkhAHIzbz3VCHd/R4osi1L1Tg/Q==",
      "dev": true,
      "requires": {
        "hosted-git-info": "^4.0.1",
        "semver": "^7.3.4",
        "validate-npm-package-name": "^3.0.0"
      }
    },
    "npm-packlist": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/npm-packlist/-/npm-packlist-3.0.0.tgz",
      "integrity": "sha512-L/cbzmutAwII5glUcf2DBRNY/d0TFd4e/FnaZigJV6JD85RHZXJFGwCndjMWiiViiWSsWt3tiOLpI3ByTnIdFQ==",
      "dev": true,
      "requires": {
        "glob": "^7.1.6",
        "ignore-walk": "^4.0.1",
        "npm-bundled": "^1.1.1",
        "npm-normalize-package-bin": "^1.0.1"
      }
    },
    "npm-pick-manifest": {
      "version": "6.1.1",
      "resolved": "https://registry.npmjs.org/npm-pick-manifest/-/npm-pick-manifest-6.1.1.tgz",
      "integrity": "sha512-dBsdBtORT84S8V8UTad1WlUyKIY9iMsAmqxHbLdeEeBNMLQDlDWWra3wYUx9EBEIiG/YwAy0XyNHDd2goAsfuA==",
      "dev": true,
      "requires": {
        "npm-install-checks": "^4.0.0",
        "npm-normalize-package-bin": "^1.0.1",
        "npm-package-arg": "^8.1.2",
        "semver": "^7.3.4"
      }
    },
    "npm-registry-fetch": {
      "version": "11.0.0",
      "resolved": "https://registry.npmjs.org/npm-registry-fetch/-/npm-registry-fetch-11.0.0.tgz",
      "integrity": "sha512-jmlgSxoDNuhAtxUIG6pVwwtz840i994dL14FoNVZisrmZW5kWd63IUTNv1m/hyRSGSqWjCUp/YZlS1BJyNp9XA==",
      "dev": true,
      "requires": {
        "make-fetch-happen": "^9.0.1",
        "minipass": "^3.1.3",
        "minipass-fetch": "^1.3.0",
        "minipass-json-stream": "^1.0.1",
        "minizlib": "^2.0.0",
        "npm-package-arg": "^8.0.0"
      }
    },
    "npm-run-path": {
      "version": "4.0.1",
      "resolved": "https://registry.npmjs.org/npm-run-path/-/npm-run-path-4.0.1.tgz",
      "integrity": "sha512-S48WzZW777zhNIrn7gxOlISNAqi9ZC/uQFnRdbeIHhZhCA6UqpkOT8T1G7BvfdgP4Er8gF4sUbaS0i7QvIfCWw==",
      "dev": true,
      "requires": {
        "path-key": "^3.0.0"
      }
    },
    "npmlog": {
      "version": "6.0.0",
      "resolved": "https://registry.npmjs.org/npmlog/-/npmlog-6.0.0.tgz",
      "integrity": "sha512-03ppFRGlsyUaQFbGC2C8QWJN/C/K7PsfyD9aQdhVKAQIH4sQBc8WASqFBP7O+Ut4d2oo5LoeoboB3cGdBZSp6Q==",
      "dev": true,
      "requires": {
        "are-we-there-yet": "^2.0.0",
        "console-control-strings": "^1.1.0",
        "gauge": "^4.0.0",
        "set-blocking": "^2.0.0"
      }
    },
    "nth-check": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/nth-check/-/nth-check-2.0.1.tgz",
      "integrity": "sha512-it1vE95zF6dTT9lBsYbxvqh0Soy4SPowchj0UBGj/V6cTPnXXtQOPUbhZ6CmGzAD/rW22LQK6E96pcdJXk4A4w==",
      "dev": true,
      "requires": {
        "boolbase": "^1.0.0"
      }
    },
    "object-assign": {
      "version": "4.1.1",
      "resolved": "https://registry.npmjs.org/object-assign/-/object-assign-4.1.1.tgz",
      "integrity": "sha1-IQmtx5ZYh8/AXLvUQsrIv7s2CGM="
    },
    "object-is": {
      "version": "1.1.5",
      "resolved": "https://registry.npmjs.org/object-is/-/object-is-1.1.5.tgz",
      "integrity": "sha512-3cyDsyHgtmi7I7DfSSI2LDp6SK2lwvtbg0p0R1e0RvTqF5ceGx+K2dfSjm1bKDMVCFEDAQvy+o8c6a7VujOddw==",
      "dev": true,
      "requires": {
        "call-bind": "^1.0.2",
        "define-properties": "^1.1.3"
      }
    },
    "object-keys": {
      "version": "1.1.1",
      "resolved": "https://registry.npmjs.org/object-keys/-/object-keys-1.1.1.tgz",
      "integrity": "sha512-NuAESUOUMrlIXOfHKzD6bpPu3tYt3xvjNdRIQ+FeT0lNb4K8WR70CaDxhuNguS2XG+GjkyMwOzsN5ZktImfhLA==",
      "dev": true
    },
    "object.assign": {
      "version": "4.1.2",
      "resolved": "https://registry.npmjs.org/object.assign/-/object.assign-4.1.2.tgz",
      "integrity": "sha512-ixT2L5THXsApyiUPYKmW+2EHpXXe5Ii3M+f4e+aJFAHao5amFRW6J0OO6c/LU8Be47utCx2GL89hxGB6XSmKuQ==",
      "dev": true,
      "requires": {
        "call-bind": "^1.0.0",
        "define-properties": "^1.1.3",
        "has-symbols": "^1.0.1",
        "object-keys": "^1.1.1"
      }
    },
    "obuf": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/obuf/-/obuf-1.1.2.tgz",
      "integrity": "sha512-PX1wu0AmAdPqOL1mWhqmlOd8kOIZQwGZw6rh7uby9fTc5lhaOWFLX3I6R1hrF9k3zUY40e6igsLGkDXK92LJNg==",
      "dev": true
    },
    "on-finished": {
      "version": "2.3.0",
      "resolved": "https://registry.npmjs.org/on-finished/-/on-finished-2.3.0.tgz",
      "integrity": "sha1-IPEzZIGwg811M3mSoWlxqi2QaUc=",
      "requires": {
        "ee-first": "1.1.1"
      }
    },
    "on-headers": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/on-headers/-/on-headers-1.0.2.tgz",
      "integrity": "sha512-pZAE+FJLoyITytdqK0U5s+FIpjN0JP3OzFi/u8Rx+EV5/W+JTWGXG8xFzevE7AjBfDqHv/8vL8qQsIhHnqRkrA=="
    },
    "once": {
      "version": "1.4.0",
      "resolved": "https://registry.npmjs.org/once/-/once-1.4.0.tgz",
      "integrity": "sha1-WDsap3WWHUsROsF9nFC6753Xa9E=",
      "requires": {
        "wrappy": "1"
      }
    },
    "onetime": {
      "version": "5.1.2",
      "resolved": "https://registry.npmjs.org/onetime/-/onetime-5.1.2.tgz",
      "integrity": "sha512-kbpaSSGJTWdAY5KPVeMOKXSrPtr8C8C7wodJbcsd51jRnmD+GZu8Y0VoU6Dm5Z4vWr0Ig/1NKuWRKf7j5aaYSg==",
      "dev": true,
      "requires": {
        "mimic-fn": "^2.1.0"
      }
    },
    "open": {
      "version": "8.4.0",
      "resolved": "https://registry.npmjs.org/open/-/open-8.4.0.tgz",
      "integrity": "sha512-XgFPPM+B28FtCCgSb9I+s9szOC1vZRSwgWsRUA5ylIxRTgKozqjOCrVOqGsYABPYK5qnfqClxZTFBa8PKt2v6Q==",
      "dev": true,
      "requires": {
        "define-lazy-prop": "^2.0.0",
        "is-docker": "^2.1.1",
        "is-wsl": "^2.2.0"
      }
    },
    "ora": {
      "version": "5.4.1",
      "resolved": "https://registry.npmjs.org/ora/-/ora-5.4.1.tgz",
      "integrity": "sha512-5b6Y85tPxZZ7QytO+BQzysW31HJku27cRIlkbAXaNx+BdcVi+LlRFmVXzeF6a7JCwJpyw5c4b+YSVImQIrBpuQ==",
      "dev": true,
      "requires": {
        "bl": "^4.1.0",
        "chalk": "^4.1.0",
        "cli-cursor": "^3.1.0",
        "cli-spinners": "^2.5.0",
        "is-interactive": "^1.0.0",
        "is-unicode-supported": "^0.1.0",
        "log-symbols": "^4.1.0",
        "strip-ansi": "^6.0.0",
        "wcwidth": "^1.0.1"
      },
      "dependencies": {
        "ansi-styles": {
          "version": "4.3.0",
          "resolved": "https://registry.npmjs.org/ansi-styles/-/ansi-styles-4.3.0.tgz",
          "integrity": "sha512-zbB9rCJAT1rbjiVDb2hqKFHNYLxgtk8NURxZ3IZwD3F6NtxbXZQCnnSi1Lkx+IDohdPlFp222wVALIheZJQSEg==",
          "dev": true,
          "requires": {
            "color-convert": "^2.0.1"
          }
        },
        "chalk": {
          "version": "4.1.2",
          "resolved": "https://registry.npmjs.org/chalk/-/chalk-4.1.2.tgz",
          "integrity": "sha512-oKnbhFyRIXpUuez8iBMmyEa4nbj4IOQyuhc/wy9kY7/WVPcwIO9VA668Pu8RkO7+0G76SLROeyw9CpQ061i4mA==",
          "dev": true,
          "requires": {
            "ansi-styles": "^4.1.0",
            "supports-color": "^7.1.0"
          }
        },
        "color-convert": {
          "version": "2.0.1",
          "resolved": "https://registry.npmjs.org/color-convert/-/color-convert-2.0.1.tgz",
          "integrity": "sha512-RRECPsj7iu/xb5oKYcsFHSppFNnsj/52OVTRKb4zP5onXwVF3zVmmToNcOfGC+CRDpfK/U584fMg38ZHCaElKQ==",
          "dev": true,
          "requires": {
            "color-name": "~1.1.4"
          }
        },
        "color-name": {
          "version": "1.1.4",
          "resolved": "https://registry.npmjs.org/color-name/-/color-name-1.1.4.tgz",
          "integrity": "sha512-dOy+3AuW3a2wNbZHIuMZpTcgjGuLU/uBL/ubcZF9OXbDo8ff4O8yVp5Bf0efS8uEoYo5q4Fx7dY9OgQGXgAsQA==",
          "dev": true
        },
        "has-flag": {
          "version": "4.0.0",
          "resolved": "https://registry.npmjs.org/has-flag/-/has-flag-4.0.0.tgz",
          "integrity": "sha512-EykJT/Q1KjTWctppgIAgfSO0tKVuZUjhgMr17kqTumMl6Afv3EISleU7qZUzoXDFTAHTDC4NOoG/ZxU3EvlMPQ==",
          "dev": true
        },
        "supports-color": {
          "version": "7.2.0",
          "resolved": "https://registry.npmjs.org/supports-color/-/supports-color-7.2.0.tgz",
          "integrity": "sha512-qpCAvRl9stuOHveKsn7HncJRvv501qIacKzQlO/+Lwxc9+0q2wLyv4Dfvt80/DPn2pqOBsJdDiogXGR9+OvwRw==",
          "dev": true,
          "requires": {
            "has-flag": "^4.0.0"
          }
        }
      }
    },
    "os-tmpdir": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/os-tmpdir/-/os-tmpdir-1.0.2.tgz",
      "integrity": "sha1-u+Z0BseaqFxc/sdm/lc0VV36EnQ=",
      "dev": true
    },
    "p-cancelable": {
      "version": "1.1.0",
      "resolved": "https://registry.npmjs.org/p-cancelable/-/p-cancelable-1.1.0.tgz",
      "integrity": "sha512-s73XxOZ4zpt1edZYZzvhqFa6uvQc1vwUa0K0BdtIZgQMAJj9IbebH+JkgKZc9h+B05PKHLOTl4ajG1BmNrVZlw=="
    },
    "p-limit": {
      "version": "2.3.0",
      "resolved": "https://registry.npmjs.org/p-limit/-/p-limit-2.3.0.tgz",
      "integrity": "sha512-//88mFWSJx8lxCzwdAABTJL2MyWB12+eIY7MDL2SqLmAkeKU9qxRvWuSyTjm3FUmpBEMuFfckAIqEaVGUDxb6w==",
      "dev": true,
      "requires": {
        "p-try": "^2.0.0"
      }
    },
    "p-locate": {
      "version": "4.1.0",
      "resolved": "https://registry.npmjs.org/p-locate/-/p-locate-4.1.0.tgz",
      "integrity": "sha512-R79ZZ/0wAxKGu3oYMlz8jy/kbhsNrS7SKZ7PxEHBgJ5+F2mtFW2fK2cOtBh1cHYkQsbzFV7I+EoRKe6Yt0oK7A==",
      "dev": true,
      "requires": {
        "p-limit": "^2.2.0"
      }
    },
    "p-map": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/p-map/-/p-map-4.0.0.tgz",
      "integrity": "sha512-/bjOqmgETBYB5BoEeGVea8dmvHb2m9GLy1E9W43yeyfP6QQCZGFNa+XRceJEuDB6zqr+gKpIAmlLebMpykw/MQ==",
      "dev": true,
      "requires": {
        "aggregate-error": "^3.0.0"
      }
    },
    "p-retry": {
      "version": "4.6.1",
      "resolved": "https://registry.npmjs.org/p-retry/-/p-retry-4.6.1.tgz",
      "integrity": "sha512-e2xXGNhZOZ0lfgR9kL34iGlU8N/KO0xZnQxVEwdeOvpqNDQfdnxIYizvWtK8RglUa3bGqI8g0R/BdfzLMxRkiA==",
      "dev": true,
      "requires": {
        "@types/retry": "^0.12.0",
        "retry": "^0.13.1"
      },
      "dependencies": {
        "retry": {
          "version": "0.13.1",
          "resolved": "https://registry.npmjs.org/retry/-/retry-0.13.1.tgz",
          "integrity": "sha512-XQBQ3I8W1Cge0Seh+6gjj03LbmRFWuoszgK9ooCpwYIrhhoO80pfq4cUkU5DkknwfOfFteRwlZ56PYOGYyFWdg==",
          "dev": true
        }
      }
    },
    "p-try": {
      "version": "2.2.0",
      "resolved": "https://registry.npmjs.org/p-try/-/p-try-2.2.0.tgz",
      "integrity": "sha512-R4nPAVTAU0B9D35/Gk3uJf/7XYbQcyohSKdvAxIRSNghFl4e71hVoGnBNQz9cWaXxO2I10KTC+3jMdvvoKw6dQ==",
      "dev": true
    },
    "package-json": {
      "version": "6.5.0",
      "resolved": "https://registry.npmjs.org/package-json/-/package-json-6.5.0.tgz",
      "integrity": "sha512-k3bdm2n25tkyxcjSKzB5x8kfVxlMdgsbPr0GkZcwHsLpba6cBjqCt1KlcChKEvxHIcTB1FVMuwoijZ26xex5MQ==",
      "requires": {
        "got": "^9.6.0",
        "registry-auth-token": "^4.0.0",
        "registry-url": "^5.0.0",
        "semver": "^6.2.0"
      },
      "dependencies": {
        "semver": {
          "version": "6.3.0",
          "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.0.tgz",
          "integrity": "sha512-b39TBaTSfV6yBrapU89p5fKekE2m/NwnDocOVruQFS1/veMgdzuPcnOM34M6CwxW8jH/lxEa5rBoDeUwu5HHTw=="
        }
      }
    },
    "pacote": {
      "version": "12.0.2",
      "resolved": "https://registry.npmjs.org/pacote/-/pacote-12.0.2.tgz",
      "integrity": "sha512-Ar3mhjcxhMzk+OVZ8pbnXdb0l8+pimvlsqBGRNkble2NVgyqOGE3yrCGi/lAYq7E7NRDMz89R1Wx5HIMCGgeYg==",
      "dev": true,
      "requires": {
        "@npmcli/git": "^2.1.0",
        "@npmcli/installed-package-contents": "^1.0.6",
        "@npmcli/promise-spawn": "^1.2.0",
        "@npmcli/run-script": "^2.0.0",
        "cacache": "^15.0.5",
        "chownr": "^2.0.0",
        "fs-minipass": "^2.1.0",
        "infer-owner": "^1.0.4",
        "minipass": "^3.1.3",
        "mkdirp": "^1.0.3",
        "npm-package-arg": "^8.0.1",
        "npm-packlist": "^3.0.0",
        "npm-pick-manifest": "^6.0.0",
        "npm-registry-fetch": "^11.0.0",
        "promise-retry": "^2.0.1",
        "read-package-json-fast": "^2.0.1",
        "rimraf": "^3.0.2",
        "ssri": "^8.0.1",
        "tar": "^6.1.0"
      }
    },
    "pako": {
      "version": "1.0.11",
      "resolved": "https://registry.npmjs.org/pako/-/pako-1.0.11.tgz",
      "integrity": "sha512-4hLB8Py4zZce5s4yd9XzopqwVv/yGNhV1Bl8NTmCq1763HeK2+EwVTv+leGeL13Dnh2wfbqowVPXCIO0z4taYw==",
      "dev": true
    },
    "parent-module": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/parent-module/-/parent-module-1.0.1.tgz",
      "integrity": "sha512-GQ2EWRpQV8/o+Aw8YqtfZZPfNRWZYkbidE9k5rpl/hC3vtHHBfGm2Ifi6qWV+coDGkrUKZAxE3Lot5kcsRlh+g==",
      "dev": true,
      "requires": {
        "callsites": "^3.0.0"
      }
    },
    "parse-json": {
      "version": "5.2.0",
      "resolved": "https://registry.npmjs.org/parse-json/-/parse-json-5.2.0.tgz",
      "integrity": "sha512-ayCKvm/phCGxOkYRSCM82iDwct8/EonSEgCSxWxD7ve6jHggsFl4fZVQBPRNgQoKiuV/odhFrGzQXZwbifC8Rg==",
      "dev": true,
      "requires": {
        "@babel/code-frame": "^7.0.0",
        "error-ex": "^1.3.1",
        "json-parse-even-better-errors": "^2.3.0",
        "lines-and-columns": "^1.1.6"
      }
    },
    "parse-node-version": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/parse-node-version/-/parse-node-version-1.0.1.tgz",
      "integrity": "sha512-3YHlOa/JgH6Mnpr05jP9eDG254US9ek25LyIxZlDItp2iJtwyaXQb57lBYLdT3MowkUFYEV2XXNAYIPlESvJlA==",
      "dev": true
    },
    "parse5": {
      "version": "6.0.1",
      "resolved": "https://registry.npmjs.org/parse5/-/parse5-6.0.1.tgz",
      "integrity": "sha512-Ofn/CTFzRGTTxwpNEs9PP93gXShHcTq255nzRYSKe8AkVpZY7e1fpmTfOyoIvjP5HG7Z2ZM7VS9PPhQGW2pOpw==",
      "dev": true
    },
    "parse5-html-rewriting-stream": {
      "version": "6.0.1",
      "resolved": "https://registry.npmjs.org/parse5-html-rewriting-stream/-/parse5-html-rewriting-stream-6.0.1.tgz",
      "integrity": "sha512-vwLQzynJVEfUlURxgnf51yAJDQTtVpNyGD8tKi2Za7m+akukNHxCcUQMAa/mUGLhCeicFdpy7Tlvj8ZNKadprg==",
      "dev": true,
      "requires": {
        "parse5": "^6.0.1",
        "parse5-sax-parser": "^6.0.1"
      }
    },
    "parse5-htmlparser2-tree-adapter": {
      "version": "6.0.1",
      "resolved": "https://registry.npmjs.org/parse5-htmlparser2-tree-adapter/-/parse5-htmlparser2-tree-adapter-6.0.1.tgz",
      "integrity": "sha512-qPuWvbLgvDGilKc5BoicRovlT4MtYT6JfJyBOMDsKoiT+GiuP5qyrPCnR9HcPECIJJmZh5jRndyNThnhhb/vlA==",
      "dev": true,
      "requires": {
        "parse5": "^6.0.1"
      }
    },
    "parse5-sax-parser": {
      "version": "6.0.1",
      "resolved": "https://registry.npmjs.org/parse5-sax-parser/-/parse5-sax-parser-6.0.1.tgz",
      "integrity": "sha512-kXX+5S81lgESA0LsDuGjAlBybImAChYRMT+/uKCEXFBFOeEhS52qUCydGhU3qLRD8D9DVjaUo821WK7DM4iCeg==",
      "dev": true,
      "requires": {
        "parse5": "^6.0.1"
      }
    },
    "parseurl": {
      "version": "1.3.3",
      "resolved": "https://registry.npmjs.org/parseurl/-/parseurl-1.3.3.tgz",
      "integrity": "sha512-CiyeOxFT/JZyN5m0z9PfXw4SCBJ6Sygz1Dpl0wqjlhDEGGBP1GnsUVEL0p63hoG1fcj3fHynXi9NYO4nWOL+qQ=="
    },
    "path-exists": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/path-exists/-/path-exists-4.0.0.tgz",
      "integrity": "sha512-ak9Qy5Q7jYb2Wwcey5Fpvg2KoAc/ZIhLSLOSBmRmygPsGwkVVt0fZa0qrtMz+m6tJTAHfZQ8FnmB4MG4LWy7/w==",
      "dev": true
    },
    "path-is-absolute": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/path-is-absolute/-/path-is-absolute-1.0.1.tgz",
      "integrity": "sha1-F0uSaHNVNP+8es5r9TpanhtcX18=",
      "dev": true
    },
    "path-key": {
      "version": "3.1.1",
      "resolved": "https://registry.npmjs.org/path-key/-/path-key-3.1.1.tgz",
      "integrity": "sha512-ojmeN0qd+y0jszEtoY48r0Peq5dwMEkIlCOu6Q5f41lfkswXuKtYrhgoTpLnyIcHm24Uhqx+5Tqm2InSwLhE6Q==",
      "dev": true
    },
    "path-parse": {
      "version": "1.0.7",
      "resolved": "https://registry.npmjs.org/path-parse/-/path-parse-1.0.7.tgz",
      "integrity": "sha512-LDJzPVEEEPR+y48z93A0Ed0yXb8pAByGWo/k5YYdYgpY2/2EsOsksJrq7lOHxryrVOn1ejG6oAp8ahvOIQD8sw==",
      "dev": true
    },
    "path-to-regexp": {
      "version": "0.1.7",
      "resolved": "https://registry.npmjs.org/path-to-regexp/-/path-to-regexp-0.1.7.tgz",
      "integrity": "sha1-32BBeABfUi8V60SQ5yR6G/qmf4w="
    },
    "path-type": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/path-type/-/path-type-4.0.0.tgz",
      "integrity": "sha512-gDKb8aZMDeD/tZWs9P6+q0J9Mwkdl6xMV8TjnGP3qJVJ06bdMgkbBlLU8IdfOsIsFz2BW1rNVT3XuNEl8zPAvw==",
      "dev": true
    },
    "picocolors": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/picocolors/-/picocolors-1.0.0.tgz",
      "integrity": "sha512-1fygroTLlHu66zi26VoTDv8yRgm0Fccecssto+MhsZ0D/DGW2sm8E8AjW7NU5VVTRt5GxbeZ5qBuJr+HyLYkjQ==",
      "dev": true
    },
    "picomatch": {
      "version": "2.3.1",
      "resolved": "https://registry.npmjs.org/picomatch/-/picomatch-2.3.1.tgz",
      "integrity": "sha512-JU3teHTNjmE2VCGFzuY8EXzCDVwEqB2a8fsIvwaStHhAWJEeVd1o1QD80CU6+ZdEXXSLbSsuLwJjkCBWqRQUVA==",
      "dev": true
    },
    "pify": {
      "version": "2.3.0",
      "resolved": "https://registry.npmjs.org/pify/-/pify-2.3.0.tgz",
      "integrity": "sha1-7RQaasBDqEnqWISY59yosVMw6Qw=",
      "dev": true
    },
    "piscina": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/piscina/-/piscina-3.1.0.tgz",
      "integrity": "sha512-KTW4sjsCD34MHrUbx9eAAbuUSpVj407hQSgk/6Epkg0pbRBmv4a3UX7Sr8wxm9xYqQLnsN4mFOjqGDzHAdgKQg==",
      "dev": true,
      "requires": {
        "eventemitter-asyncresource": "^1.0.0",
        "hdr-histogram-js": "^2.0.1",
        "hdr-histogram-percentiles-obj": "^3.0.0",
        "nice-napi": "^1.0.2"
      }
    },
    "pkg-dir": {
      "version": "4.2.0",
      "resolved": "https://registry.npmjs.org/pkg-dir/-/pkg-dir-4.2.0.tgz",
      "integrity": "sha512-HRDzbaKjC+AOWVXxAU/x54COGeIv9eb+6CkDSQoNTt4XyWoIJvuPsXizxu/Fr23EiekbtZwmh1IcIG/l/a10GQ==",
      "dev": true,
      "requires": {
        "find-up": "^4.0.0"
      }
    },
    "please-upgrade-node": {
      "version": "3.2.0",
      "resolved": "https://registry.npmjs.org/please-upgrade-node/-/please-upgrade-node-3.2.0.tgz",
      "integrity": "sha512-gQR3WpIgNIKwBMVLkpMUeR3e1/E1y42bqDQZfql+kDeXd8COYfM8PQA4X6y7a8u9Ua9FHmsrrmirW2vHs45hWg==",
      "requires": {
        "semver-compare": "^1.0.0"
      }
    },
    "pluralize": {
      "version": "8.0.0",
      "resolved": "https://registry.npmjs.org/pluralize/-/pluralize-8.0.0.tgz",
      "integrity": "sha512-Nc3IT5yHzflTfbjgqWcCPpo7DaKy4FnpB0l/zCAW0Tc7jxAiuqSxHasntB3D7887LSrA93kDJ9IXovxJYxyLCA=="
    },
    "portfinder": {
      "version": "1.0.28",
      "resolved": "https://registry.npmjs.org/portfinder/-/portfinder-1.0.28.tgz",
      "integrity": "sha512-Se+2isanIcEqf2XMHjyUKskczxbPH7dQnlMjXX6+dybayyHvAf/TCgyMRlzf/B6QDhAEFOGes0pzRo3by4AbMA==",
      "dev": true,
      "requires": {
        "async": "^2.6.2",
        "debug": "^3.1.1",
        "mkdirp": "^0.5.5"
      },
      "dependencies": {
        "debug": {
          "version": "3.2.7",
          "resolved": "https://registry.npmjs.org/debug/-/debug-3.2.7.tgz",
          "integrity": "sha512-CFjzYYAi4ThfiQvizrFQevTTXHtnCqWfe7x1AhgEscTz6ZbLbfoLRLPugTQyBth6f8ZERVUSyWHFD/7Wu4t1XQ==",
          "dev": true,
          "requires": {
            "ms": "^2.1.1"
          }
        },
        "mkdirp": {
          "version": "0.5.5",
          "resolved": "https://registry.npmjs.org/mkdirp/-/mkdirp-0.5.5.tgz",
          "integrity": "sha512-NKmAlESf6jMGym1++R0Ra7wvhV+wFW63FaSOFPwRahvea0gMUcGUhVeAg/0BC0wiv9ih5NYPB1Wn1UEI1/L+xQ==",
          "dev": true,
          "requires": {
            "minimist": "^1.2.5"
          }
        }
      }
    },
    "postcss": {
      "version": "8.4.4",
      "resolved": "https://registry.npmjs.org/postcss/-/postcss-8.4.4.tgz",
      "integrity": "sha512-joU6fBsN6EIer28Lj6GDFoC/5yOZzLCfn0zHAn/MYXI7aPt4m4hK5KC5ovEZXy+lnCjmYIbQWngvju2ddyEr8Q==",
      "dev": true,
      "requires": {
        "nanoid": "^3.1.30",
        "picocolors": "^1.0.0",
        "source-map-js": "^1.0.1"
      }
    },
    "postcss-attribute-case-insensitive": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/postcss-attribute-case-insensitive/-/postcss-attribute-case-insensitive-5.0.0.tgz",
      "integrity": "sha512-b4g9eagFGq9T5SWX4+USfVyjIb3liPnjhHHRMP7FMB2kFVpYyfEscV0wP3eaXhKlcHKUut8lt5BGoeylWA/dBQ==",
      "dev": true,
      "requires": {
        "postcss-selector-parser": "^6.0.2"
      }
    },
    "postcss-color-functional-notation": {
      "version": "4.2.1",
      "resolved": "https://registry.npmjs.org/postcss-color-functional-notation/-/postcss-color-functional-notation-4.2.1.tgz",
      "integrity": "sha512-62OBIXCjRXpQZcFOYIXwXBlpAVWrYk8ek1rcjvMING4Q2cf0ipyN9qT+BhHA6HmftGSEnFQu2qgKO3gMscl3Rw==",
      "dev": true,
      "requires": {
        "postcss-value-parser": "^4.2.0"
      }
    },
    "postcss-color-hex-alpha": {
      "version": "8.0.2",
      "resolved": "https://registry.npmjs.org/postcss-color-hex-alpha/-/postcss-color-hex-alpha-8.0.2.tgz",
      "integrity": "sha512-gyx8RgqSmGVK156NAdKcsfkY3KPGHhKqvHTL3hhveFrBBToguKFzhyiuk3cljH6L4fJ0Kv+JENuPXs1Wij27Zw==",
      "dev": true,
      "requires": {
        "postcss-value-parser": "^4.2.0"
      }
    },
    "postcss-color-rebeccapurple": {
      "version": "7.0.2",
      "resolved": "https://registry.npmjs.org/postcss-color-rebeccapurple/-/postcss-color-rebeccapurple-7.0.2.tgz",
      "integrity": "sha512-SFc3MaocHaQ6k3oZaFwH8io6MdypkUtEy/eXzXEB1vEQlO3S3oDc/FSZA8AsS04Z25RirQhlDlHLh3dn7XewWw==",
      "dev": true,
      "requires": {
        "postcss-value-parser": "^4.2.0"
      }
    },
    "postcss-custom-media": {
      "version": "8.0.0",
      "resolved": "https://registry.npmjs.org/postcss-custom-media/-/postcss-custom-media-8.0.0.tgz",
      "integrity": "sha512-FvO2GzMUaTN0t1fBULDeIvxr5IvbDXcIatt6pnJghc736nqNgsGao5NT+5+WVLAQiTt6Cb3YUms0jiPaXhL//g==",
      "dev": true,
      "requires": {}
    },
    "postcss-custom-properties": {
      "version": "12.1.3",
      "resolved": "https://registry.npmjs.org/postcss-custom-properties/-/postcss-custom-properties-12.1.3.tgz",
      "integrity": "sha512-rtu3otIeY532PnEuuBrIIe+N+pcdbX/7JMZfrcL09wc78YayrHw5E8UkDfvnlOhEUrI4ptCuzXQfj+Or6spbGA==",
      "dev": true,
      "requires": {
        "postcss-value-parser": "^4.2.0"
      }
    },
    "postcss-custom-selectors": {
      "version": "6.0.0",
      "resolved": "https://registry.npmjs.org/postcss-custom-selectors/-/postcss-custom-selectors-6.0.0.tgz",
      "integrity": "sha512-/1iyBhz/W8jUepjGyu7V1OPcGbc636snN1yXEQCinb6Bwt7KxsiU7/bLQlp8GwAXzCh7cobBU5odNn/2zQWR8Q==",
      "dev": true,
      "requires": {
        "postcss-selector-parser": "^6.0.4"
      }
    },
    "postcss-dir-pseudo-class": {
      "version": "6.0.3",
      "resolved": "https://registry.npmjs.org/postcss-dir-pseudo-class/-/postcss-dir-pseudo-class-6.0.3.tgz",
      "integrity": "sha512-qiPm+CNAlgXiMf0J5IbBBEXA9l/Q5HGsNGkL3znIwT2ZFRLGY9U2fTUpa4lqCUXQOxaLimpacHeQC80BD2qbDw==",
      "dev": true,
      "requires": {
        "postcss-selector-parser": "^6.0.8"
      }
    },
    "postcss-double-position-gradients": {
      "version": "3.0.4",
      "resolved": "https://registry.npmjs.org/postcss-double-position-gradients/-/postcss-double-position-gradients-3.0.4.tgz",
      "integrity": "sha512-qz+s5vhKJlsHw8HjSs+HVk2QGFdRyC68KGRQGX3i+GcnUjhWhXQEmCXW6siOJkZ1giu0ddPwSO6I6JdVVVPoog==",
      "dev": true,
      "requires": {
        "postcss-value-parser": "^4.2.0"
      }
    },
    "postcss-env-function": {
      "version": "4.0.4",
      "resolved": "https://registry.npmjs.org/postcss-env-function/-/postcss-env-function-4.0.4.tgz",
      "integrity": "sha512-0ltahRTPtXSIlEZFv7zIvdEib7HN0ZbUQxrxIKn8KbiRyhALo854I/CggU5lyZe6ZBvSTJ6Al2vkZecI2OhneQ==",
      "dev": true,
      "requires": {
        "postcss-value-parser": "^4.2.0"
      }
    },
    "postcss-focus-visible": {
      "version": "6.0.3",
      "resolved": "https://registry.npmjs.org/postcss-focus-visible/-/postcss-focus-visible-6.0.3.tgz",
      "integrity": "sha512-ozOsg+L1U8S+rxSHnJJiET6dNLyADcPHhEarhhtCI9DBLGOPG/2i4ddVoFch9LzrBgb8uDaaRI4nuid2OM82ZA==",
      "dev": true,
      "requires": {
        "postcss-selector-parser": "^6.0.8"
      }
    },
    "postcss-focus-within": {
      "version": "5.0.3",
      "resolved": "https://registry.npmjs.org/postcss-focus-within/-/postcss-focus-within-5.0.3.tgz",
      "integrity": "sha512-fk9y2uFS6/Kpp7/A9Hz9Z4rlFQ8+tzgBcQCXAFSrXFGAbKx+4ZZOmmfHuYjCOMegPWoz0pnC6fNzi8j7Xyqp5Q==",
      "dev": true,
      "requires": {
        "postcss-selector-parser": "^6.0.8"
      }
    },
    "postcss-font-variant": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/postcss-font-variant/-/postcss-font-variant-5.0.0.tgz",
      "integrity": "sha512-1fmkBaCALD72CK2a9i468mA/+tr9/1cBxRRMXOUaZqO43oWPR5imcyPjXwuv7PXbCid4ndlP5zWhidQVVa3hmA==",
      "dev": true,
      "requires": {}
    },
    "postcss-gap-properties": {
      "version": "3.0.2",
      "resolved": "https://registry.npmjs.org/postcss-gap-properties/-/postcss-gap-properties-3.0.2.tgz",
      "integrity": "sha512-EaMy/pbxtQnKDsnbEjdqlkCkROTQZzolcLKgIE+3b7EuJfJydH55cZeHfm+MtIezXRqhR80VKgaztO/vHq94Fw==",
      "dev": true,
      "requires": {}
    },
    "postcss-image-set-function": {
      "version": "4.0.4",
      "resolved": "https://registry.npmjs.org/postcss-image-set-function/-/postcss-image-set-function-4.0.4.tgz",
      "integrity": "sha512-BlEo9gSTj66lXjRNByvkMK9dEdEGFXRfGjKRi9fo8s0/P3oEk74cAoonl/utiM50E2OPVb/XSu+lWvdW4KtE/Q==",
      "dev": true,
      "requires": {
        "postcss-value-parser": "^4.2.0"
      }
    },
    "postcss-import": {
      "version": "14.0.2",
      "resolved": "https://registry.npmjs.org/postcss-import/-/postcss-import-14.0.2.tgz",
      "integrity": "sha512-BJ2pVK4KhUyMcqjuKs9RijV5tatNzNa73e/32aBVE/ejYPe37iH+6vAu9WvqUkB5OAYgLHzbSvzHnorybJCm9g==",
      "dev": true,
      "requires": {
        "postcss-value-parser": "^4.0.0",
        "read-cache": "^1.0.0",
        "resolve": "^1.1.7"
      }
    },
    "postcss-initial": {
      "version": "4.0.1",
      "resolved": "https://registry.npmjs.org/postcss-initial/-/postcss-initial-4.0.1.tgz",
      "integrity": "sha512-0ueD7rPqX8Pn1xJIjay0AZeIuDoF+V+VvMt/uOnn+4ezUKhZM/NokDeP6DwMNyIoYByuN/94IQnt5FEkaN59xQ==",
      "dev": true,
      "requires": {}
    },
    "postcss-lab-function": {
      "version": "4.0.3",
      "resolved": "https://registry.npmjs.org/postcss-lab-function/-/postcss-lab-function-4.0.3.tgz",
      "integrity": "sha512-MH4tymWmefdZQ7uVG/4icfLjAQmH6o2NRYyVh2mKoB4RXJp9PjsyhZwhH4ouaCQHvg+qJVj3RzeAR1EQpIlXZA==",
      "dev": true,
      "requires": {
        "postcss-value-parser": "^4.2.0"
      }
    },
    "postcss-loader": {
      "version": "6.2.1",
      "resolved": "https://registry.npmjs.org/postcss-loader/-/postcss-loader-6.2.1.tgz",
      "integrity": "sha512-WbbYpmAaKcux/P66bZ40bpWsBucjx/TTgVVzRZ9yUO8yQfVBlameJ0ZGVaPfH64hNSBh63a+ICP5nqOpBA0w+Q==",
      "dev": true,
      "requires": {
        "cosmiconfig": "^7.0.0",
        "klona": "^2.0.5",
        "semver": "^7.3.5"
      }
    },
    "postcss-logical": {
      "version": "5.0.3",
      "resolved": "https://registry.npmjs.org/postcss-logical/-/postcss-logical-5.0.3.tgz",
      "integrity": "sha512-P5NcHWYrif0vK8rgOy/T87vg0WRIj3HSknrvp1wzDbiBeoDPVmiVRmkown2eSQdpPveat/MC1ess5uhzZFVnqQ==",
      "dev": true,
      "requires": {}
    },
    "postcss-media-minmax": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/postcss-media-minmax/-/postcss-media-minmax-5.0.0.tgz",
      "integrity": "sha512-yDUvFf9QdFZTuCUg0g0uNSHVlJ5X1lSzDZjPSFaiCWvjgsvu8vEVxtahPrLMinIDEEGnx6cBe6iqdx5YWz08wQ==",
      "dev": true,
      "requires": {}
    },
    "postcss-modules-extract-imports": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/postcss-modules-extract-imports/-/postcss-modules-extract-imports-3.0.0.tgz",
      "integrity": "sha512-bdHleFnP3kZ4NYDhuGlVK+CMrQ/pqUm8bx/oGL93K6gVwiclvX5x0n76fYMKuIGKzlABOy13zsvqjb0f92TEXw==",
      "dev": true,
      "requires": {}
    },
    "postcss-modules-local-by-default": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/postcss-modules-local-by-default/-/postcss-modules-local-by-default-4.0.0.tgz",
      "integrity": "sha512-sT7ihtmGSF9yhm6ggikHdV0hlziDTX7oFoXtuVWeDd3hHObNkcHRo9V3yg7vCAY7cONyxJC/XXCmmiHHcvX7bQ==",
      "dev": true,
      "requires": {
        "icss-utils": "^5.0.0",
        "postcss-selector-parser": "^6.0.2",
        "postcss-value-parser": "^4.1.0"
      }
    },
    "postcss-modules-scope": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/postcss-modules-scope/-/postcss-modules-scope-3.0.0.tgz",
      "integrity": "sha512-hncihwFA2yPath8oZ15PZqvWGkWf+XUfQgUGamS4LqoP1anQLOsOJw0vr7J7IwLpoY9fatA2qiGUGmuZL0Iqlg==",
      "dev": true,
      "requires": {
        "postcss-selector-parser": "^6.0.4"
      }
    },
    "postcss-modules-values": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/postcss-modules-values/-/postcss-modules-values-4.0.0.tgz",
      "integrity": "sha512-RDxHkAiEGI78gS2ofyvCsu7iycRv7oqw5xMWn9iMoR0N/7mf9D50ecQqUo5BZ9Zh2vH4bCUR/ktCqbB9m8vJjQ==",
      "dev": true,
      "requires": {
        "icss-utils": "^5.0.0"
      }
    },
    "postcss-nesting": {
      "version": "10.1.2",
      "resolved": "https://registry.npmjs.org/postcss-nesting/-/postcss-nesting-10.1.2.tgz",
      "integrity": "sha512-dJGmgmsvpzKoVMtDMQQG/T6FSqs6kDtUDirIfl4KnjMCiY9/ETX8jdKyCd20swSRAbUYkaBKV20pxkzxoOXLqQ==",
      "dev": true,
      "requires": {
        "postcss-selector-parser": "^6.0.8"
      }
    },
    "postcss-overflow-shorthand": {
      "version": "3.0.2",
      "resolved": "https://registry.npmjs.org/postcss-overflow-shorthand/-/postcss-overflow-shorthand-3.0.2.tgz",
      "integrity": "sha512-odBMVt6PTX7jOE9UNvmnLrFzA9pXS44Jd5shFGGtSHY80QCuJF+14McSy0iavZggRZ9Oj//C9vOKQmexvyEJMg==",
      "dev": true,
      "requires": {}
    },
    "postcss-page-break": {
      "version": "3.0.4",
      "resolved": "https://registry.npmjs.org/postcss-page-break/-/postcss-page-break-3.0.4.tgz",
      "integrity": "sha512-1JGu8oCjVXLa9q9rFTo4MbeeA5FMe00/9C7lN4va606Rdb+HkxXtXsmEDrIraQ11fGz/WvKWa8gMuCKkrXpTsQ==",
      "dev": true,
      "requires": {}
    },
    "postcss-place": {
      "version": "7.0.3",
      "resolved": "https://registry.npmjs.org/postcss-place/-/postcss-place-7.0.3.tgz",
      "integrity": "sha512-tDQ3m+GYoOar+KoQgj+pwPAvGHAp/Sby6vrFiyrELrMKQJ4AejL0NcS0mm296OKKYA2SRg9ism/hlT/OLhBrdQ==",
      "dev": true,
      "requires": {
        "postcss-value-parser": "^4.2.0"
      }
    },
    "postcss-preset-env": {
      "version": "7.2.3",
      "resolved": "https://registry.npmjs.org/postcss-preset-env/-/postcss-preset-env-7.2.3.tgz",
      "integrity": "sha512-Ok0DhLfwrcNGrBn8sNdy1uZqWRk/9FId0GiQ39W4ILop5GHtjJs8bu1MY9isPwHInpVEPWjb4CEcEaSbBLpfwA==",
      "dev": true,
      "requires": {
        "autoprefixer": "^10.4.2",
        "browserslist": "^4.19.1",
        "caniuse-lite": "^1.0.30001299",
        "css-blank-pseudo": "^3.0.2",
        "css-has-pseudo": "^3.0.3",
        "css-prefers-color-scheme": "^6.0.2",
        "cssdb": "^5.0.0",
        "postcss-attribute-case-insensitive": "^5.0.0",
        "postcss-color-functional-notation": "^4.2.1",
        "postcss-color-hex-alpha": "^8.0.2",
        "postcss-color-rebeccapurple": "^7.0.2",
        "postcss-custom-media": "^8.0.0",
        "postcss-custom-properties": "^12.1.2",
        "postcss-custom-selectors": "^6.0.0",
        "postcss-dir-pseudo-class": "^6.0.3",
        "postcss-double-position-gradients": "^3.0.4",
        "postcss-env-function": "^4.0.4",
        "postcss-focus-visible": "^6.0.3",
        "postcss-focus-within": "^5.0.3",
        "postcss-font-variant": "^5.0.0",
        "postcss-gap-properties": "^3.0.2",
        "postcss-image-set-function": "^4.0.4",
        "postcss-initial": "^4.0.1",
        "postcss-lab-function": "^4.0.3",
        "postcss-logical": "^5.0.3",
        "postcss-media-minmax": "^5.0.0",
        "postcss-nesting": "^10.1.2",
        "postcss-overflow-shorthand": "^3.0.2",
        "postcss-page-break": "^3.0.4",
        "postcss-place": "^7.0.3",
        "postcss-pseudo-class-any-link": "^7.0.2",
        "postcss-replace-overflow-wrap": "^4.0.0",
        "postcss-selector-not": "^5.0.0"
      }
    },
    "postcss-pseudo-class-any-link": {
      "version": "7.0.2",
      "resolved": "https://registry.npmjs.org/postcss-pseudo-class-any-link/-/postcss-pseudo-class-any-link-7.0.2.tgz",
      "integrity": "sha512-CG35J1COUH7OOBgpw5O+0koOLUd5N4vUGKUqSAuIe4GiuLHWU96Pqp+UPC8QITTd12zYAFx76pV7qWT/0Aj/TA==",
      "dev": true,
      "requires": {
        "postcss-selector-parser": "^6.0.8"
      }
    },
    "postcss-replace-overflow-wrap": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/postcss-replace-overflow-wrap/-/postcss-replace-overflow-wrap-4.0.0.tgz",
      "integrity": "sha512-KmF7SBPphT4gPPcKZc7aDkweHiKEEO8cla/GjcBK+ckKxiZslIu3C4GCRW3DNfL0o7yW7kMQu9xlZ1kXRXLXtw==",
      "dev": true,
      "requires": {}
    },
    "postcss-selector-not": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/postcss-selector-not/-/postcss-selector-not-5.0.0.tgz",
      "integrity": "sha512-/2K3A4TCP9orP4TNS7u3tGdRFVKqz/E6pX3aGnriPG0jU78of8wsUcqE4QAhWEU0d+WnMSF93Ah3F//vUtK+iQ==",
      "dev": true,
      "requires": {
        "balanced-match": "^1.0.0"
      }
    },
    "postcss-selector-parser": {
      "version": "6.0.9",
      "resolved": "https://registry.npmjs.org/postcss-selector-parser/-/postcss-selector-parser-6.0.9.tgz",
      "integrity": "sha512-UO3SgnZOVTwu4kyLR22UQ1xZh086RyNZppb7lLAKBFK8a32ttG5i87Y/P3+2bRSjZNyJ1B7hfFNo273tKe9YxQ==",
      "dev": true,
      "requires": {
        "cssesc": "^3.0.0",
        "util-deprecate": "^1.0.2"
      }
    },
    "postcss-value-parser": {
      "version": "4.2.0",
      "resolved": "https://registry.npmjs.org/postcss-value-parser/-/postcss-value-parser-4.2.0.tgz",
      "integrity": "sha512-1NNCs6uurfkVbeXG4S8JFT9t19m45ICnif8zWLd5oPSZ50QnwMfK+H3jv408d4jw/7Bttv5axS5IiHoLaVNHeQ==",
      "dev": true
    },
    "prepend-http": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/prepend-http/-/prepend-http-2.0.0.tgz",
      "integrity": "sha1-6SQ0v6XqjBn0HN/UAddBo8gZ2Jc="
    },
    "pretty-bytes": {
      "version": "5.6.0",
      "resolved": "https://registry.npmjs.org/pretty-bytes/-/pretty-bytes-5.6.0.tgz",
      "integrity": "sha512-FFw039TmrBqFK8ma/7OL3sDz/VytdtJr044/QUJtH0wK9lb9jLq9tJyIxUwtQJHwar2BqtiA4iCWSwo9JLkzFg==",
      "dev": true
    },
    "process-nextick-args": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/process-nextick-args/-/process-nextick-args-2.0.1.tgz",
      "integrity": "sha512-3ouUOpQhtgrbOa17J7+uxOTpITYWaGP7/AhoR3+A+/1e9skrzelGi/dXzEYyvbxubEF6Wn2ypscTKiKJFFn1ag==",
      "dev": true
    },
    "promise-inflight": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/promise-inflight/-/promise-inflight-1.0.1.tgz",
      "integrity": "sha1-mEcocL8igTL8vdhoEputEsPAKeM=",
      "dev": true
    },
    "promise-retry": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/promise-retry/-/promise-retry-2.0.1.tgz",
      "integrity": "sha512-y+WKFlBR8BGXnsNlIHFGPZmyDf3DFMoLhaflAnyZgV6rG6xu+JwesTo2Q9R6XwYmtmwAFCkAk3e35jEdoeh/3g==",
      "dev": true,
      "requires": {
        "err-code": "^2.0.2",
        "retry": "^0.12.0"
      }
    },
    "proxy-addr": {
      "version": "2.0.7",
      "resolved": "https://registry.npmjs.org/proxy-addr/-/proxy-addr-2.0.7.tgz",
      "integrity": "sha512-llQsMLSUDUPT44jdrU/O37qlnifitDP+ZwrmmZcoSKyLKvtZxpyV0n2/bD/N4tBAAZ/gJEdZU7KMraoK1+XYAg==",
      "requires": {
        "forwarded": "0.2.0",
        "ipaddr.js": "1.9.1"
      },
      "dependencies": {
        "ipaddr.js": {
          "version": "1.9.1",
          "resolved": "https://registry.npmjs.org/ipaddr.js/-/ipaddr.js-1.9.1.tgz",
          "integrity": "sha512-0KI/607xoxSToH7GjN1FfSbLoU0+btTicjsQSWQlh/hZykN8KpmMf7uYwPW3R+akZ6R/w18ZlXSHBYXiYUPO3g=="
        }
      }
    },
    "prr": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/prr/-/prr-1.0.1.tgz",
      "integrity": "sha1-0/wRS6BplaRexok/SEzrHXj19HY=",
      "dev": true,
      "optional": true
    },
    "pump": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/pump/-/pump-3.0.0.tgz",
      "integrity": "sha512-LwZy+p3SFs1Pytd/jYct4wpv49HiYCqd9Rlc5ZVdk0V+8Yzv6jR5Blk3TRmPL1ft69TxP0IMZGJ+WPFU2BFhww==",
      "requires": {
        "end-of-stream": "^1.1.0",
        "once": "^1.3.1"
      }
    },
    "punycode": {
      "version": "2.1.1",
      "resolved": "https://registry.npmjs.org/punycode/-/punycode-2.1.1.tgz",
      "integrity": "sha512-XRsRjdf+j5ml+y/6GKHPZbrF/8p2Yga0JPtdqTIY2Xe5ohJPD9saDJJLPvp9+NSBprVvevdXZybnj2cv8OEd0A==",
      "dev": true
    },
    "pupa": {
      "version": "2.1.1",
      "resolved": "https://registry.npmjs.org/pupa/-/pupa-2.1.1.tgz",
      "integrity": "sha512-l1jNAspIBSFqbT+y+5FosojNpVpF94nlI+wDUpqP9enwOTfHx9f0gh5nB96vl+6yTpsJsypeNrwfzPrKuHB41A==",
      "requires": {
        "escape-goat": "^2.0.0"
      }
    },
    "qjobs": {
      "version": "1.2.0",
      "resolved": "https://registry.npmjs.org/qjobs/-/qjobs-1.2.0.tgz",
      "integrity": "sha512-8YOJEHtxpySA3fFDyCRxA+UUV+fA+rTWnuWvylOK/NCjhY+b4ocCtmu8TtsWb+mYeU+GCHf/S66KZF/AsteKHg==",
      "dev": true
    },
    "qs": {
      "version": "6.9.6",
      "resolved": "https://registry.npmjs.org/qs/-/qs-6.9.6.tgz",
      "integrity": "sha512-TIRk4aqYLNoJUbd+g2lEdz5kLWIuTMRagAXxl78Q0RiVjAOugHmeKNGdd3cwo/ktpf9aL9epCfFqWDEKysUlLQ=="
    },
    "querystring": {
      "version": "0.2.0",
      "resolved": "https://registry.npmjs.org/querystring/-/querystring-0.2.0.tgz",
      "integrity": "sha1-sgmEkgO7Jd+CDadW50cAWHhSFiA=",
      "dev": true
    },
    "queue-microtask": {
      "version": "1.2.3",
      "resolved": "https://registry.npmjs.org/queue-microtask/-/queue-microtask-1.2.3.tgz",
      "integrity": "sha512-NuaNSa6flKT5JaSYQzJok04JzTL1CA6aGhv5rfLW3PgqA+M2ChpZQnAC8h8i4ZFkBS8X5RqkDBHA7r4hej3K9A==",
      "dev": true
    },
    "randombytes": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/randombytes/-/randombytes-2.1.0.tgz",
      "integrity": "sha512-vYl3iOX+4CKUWuxGi9Ukhie6fsqXqS9FE2Zaic4tNFD2N2QQaXOMFbuKK4QmDHC0JO6B1Zp41J0LpT0oR68amQ==",
      "dev": true,
      "requires": {
        "safe-buffer": "^5.1.0"
      }
    },
    "range-parser": {
      "version": "1.2.1",
      "resolved": "https://registry.npmjs.org/range-parser/-/range-parser-1.2.1.tgz",
      "integrity": "sha512-Hrgsx+orqoygnmhFbKaHE6c296J+HTAQXoxEF6gNupROmmGJRoyzfG3ccAveqCBrwr/2yxQ5BVd/GTl5agOwSg=="
    },
    "raw-body": {
      "version": "2.4.2",
      "resolved": "https://registry.npmjs.org/raw-body/-/raw-body-2.4.2.tgz",
      "integrity": "sha512-RPMAFUJP19WIet/99ngh6Iv8fzAbqum4Li7AD6DtGaW2RpMB/11xDoalPiJMTbu6I3hkbMVkATvZrqb9EEqeeQ==",
      "requires": {
        "bytes": "3.1.1",
        "http-errors": "1.8.1",
        "iconv-lite": "0.4.24",
        "unpipe": "1.0.0"
      }
    },
    "rc": {
      "version": "1.2.8",
      "resolved": "https://registry.npmjs.org/rc/-/rc-1.2.8.tgz",
      "integrity": "sha512-y3bGgqKj3QBdxLbLkomlohkvsA8gdAiUQlSBJnBhfn+BPxg4bc62d8TcBW15wavDfgexCgccckhcZvywyQYPOw==",
      "requires": {
        "deep-extend": "^0.6.0",
        "ini": "~1.3.0",
        "minimist": "^1.2.0",
        "strip-json-comments": "~2.0.1"
      },
      "dependencies": {
        "ini": {
          "version": "1.3.8",
          "resolved": "https://registry.npmjs.org/ini/-/ini-1.3.8.tgz",
          "integrity": "sha512-JV/yugV2uzW5iMRSiZAyDtQd+nxtUnjeLt0acNdw98kKLrvuRVyB80tsREOE7yvGVgalhZ6RNXCmEHkUKBKxew=="
        }
      }
    },
    "read-cache": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/read-cache/-/read-cache-1.0.0.tgz",
      "integrity": "sha1-5mTvMRYRZsl1HNvo28+GtftY93Q=",
      "dev": true,
      "requires": {
        "pify": "^2.3.0"
      }
    },
    "read-package-json-fast": {
      "version": "2.0.3",
      "resolved": "https://registry.npmjs.org/read-package-json-fast/-/read-package-json-fast-2.0.3.tgz",
      "integrity": "sha512-W/BKtbL+dUjTuRL2vziuYhp76s5HZ9qQhd/dKfWIZveD0O40453QNyZhC0e63lqZrAQ4jiOapVoeJ7JrszenQQ==",
      "dev": true,
      "requires": {
        "json-parse-even-better-errors": "^2.3.0",
        "npm-normalize-package-bin": "^1.0.1"
      }
    },
    "readable-stream": {
      "version": "3.6.0",
      "resolved": "https://registry.npmjs.org/readable-stream/-/readable-stream-3.6.0.tgz",
      "integrity": "sha512-BViHy7LKeTz4oNnkcLJ+lVSL6vpiFeX6/d3oSH8zCW7UxP2onchk+vTGB143xuFjHS3deTgkKoXXymXqymiIdA==",
      "dev": true,
      "requires": {
        "inherits": "^2.0.3",
        "string_decoder": "^1.1.1",
        "util-deprecate": "^1.0.1"
      }
    },
    "readdirp": {
      "version": "3.6.0",
      "resolved": "https://registry.npmjs.org/readdirp/-/readdirp-3.6.0.tgz",
      "integrity": "sha512-hOS089on8RduqdbhvQ5Z37A0ESjsqz6qnRcffsMU3495FuTdqSm+7bhJ29JvIOsBDEEnan5DPu9t3To9VRlMzA==",
      "dev": true,
      "requires": {
        "picomatch": "^2.2.1"
      }
    },
    "reflect-metadata": {
      "version": "0.1.13",
      "resolved": "https://registry.npmjs.org/reflect-metadata/-/reflect-metadata-0.1.13.tgz",
      "integrity": "sha512-Ts1Y/anZELhSsjMcU605fU9RE4Oi3p5ORujwbIKXfWa+0Zxs510Qrmrce5/Jowq3cHSZSJqBjypxmHarc+vEWg==",
      "dev": true
    },
    "regenerate": {
      "version": "1.4.2",
      "resolved": "https://registry.npmjs.org/regenerate/-/regenerate-1.4.2.tgz",
      "integrity": "sha512-zrceR/XhGYU/d/opr2EKO7aRHUeiBI8qjtfHqADTwZd6Szfy16la6kqD0MIUs5z5hx6AaKa+PixpPrR289+I0A==",
      "dev": true
    },
    "regenerate-unicode-properties": {
      "version": "9.0.0",
      "resolved": "https://registry.npmjs.org/regenerate-unicode-properties/-/regenerate-unicode-properties-9.0.0.tgz",
      "integrity": "sha512-3E12UeNSPfjrgwjkR81m5J7Aw/T55Tu7nUyZVQYCKEOs+2dkxEY+DpPtZzO4YruuiPb7NkYLVcyJC4+zCbk5pA==",
      "dev": true,
      "requires": {
        "regenerate": "^1.4.2"
      }
    },
    "regenerator-runtime": {
      "version": "0.13.9",
      "resolved": "https://registry.npmjs.org/regenerator-runtime/-/regenerator-runtime-0.13.9.tgz",
      "integrity": "sha512-p3VT+cOEgxFsRRA9X4lkI1E+k2/CtnKtU4gcxyaCUreilL/vqI6CdZ3wxVUx3UOUg+gnUOQQcRI7BmSI656MYA==",
      "dev": true
    },
    "regenerator-transform": {
      "version": "0.14.5",
      "resolved": "https://registry.npmjs.org/regenerator-transform/-/regenerator-transform-0.14.5.tgz",
      "integrity": "sha512-eOf6vka5IO151Jfsw2NO9WpGX58W6wWmefK3I1zEGr0lOD0u8rwPaNqQL1aRxUaxLeKO3ArNh3VYg1KbaD+FFw==",
      "dev": true,
      "requires": {
        "@babel/runtime": "^7.8.4"
      }
    },
    "regex-parser": {
      "version": "2.2.11",
      "resolved": "https://registry.npmjs.org/regex-parser/-/regex-parser-2.2.11.tgz",
      "integrity": "sha512-jbD/FT0+9MBU2XAZluI7w2OBs1RBi6p9M83nkoZayQXXU9e8Robt69FcZc7wU4eJD/YFTjn1JdCk3rbMJajz8Q==",
      "dev": true
    },
    "regexp.prototype.flags": {
      "version": "1.4.1",
      "resolved": "https://registry.npmjs.org/regexp.prototype.flags/-/regexp.prototype.flags-1.4.1.tgz",
      "integrity": "sha512-pMR7hBVUUGI7PMA37m2ofIdQCsomVnas+Jn5UPGAHQ+/LlwKm/aTLJHdasmHRzlfeZwHiAOaRSo2rbBDm3nNUQ==",
      "dev": true,
      "requires": {
        "call-bind": "^1.0.2",
        "define-properties": "^1.1.3"
      }
    },
    "regexpu-core": {
      "version": "4.8.0",
      "resolved": "https://registry.npmjs.org/regexpu-core/-/regexpu-core-4.8.0.tgz",
      "integrity": "sha512-1F6bYsoYiz6is+oz70NWur2Vlh9KWtswuRuzJOfeYUrfPX2o8n74AnUVaOGDbUqVGO9fNHu48/pjJO4sNVwsOg==",
      "dev": true,
      "requires": {
        "regenerate": "^1.4.2",
        "regenerate-unicode-properties": "^9.0.0",
        "regjsgen": "^0.5.2",
        "regjsparser": "^0.7.0",
        "unicode-match-property-ecmascript": "^2.0.0",
        "unicode-match-property-value-ecmascript": "^2.0.0"
      }
    },
    "registry-auth-token": {
      "version": "4.2.1",
      "resolved": "https://registry.npmjs.org/registry-auth-token/-/registry-auth-token-4.2.1.tgz",
      "integrity": "sha512-6gkSb4U6aWJB4SF2ZvLb76yCBjcvufXBqvvEx1HbmKPkutswjW1xNVRY0+daljIYRbogN7O0etYSlbiaEQyMyw==",
      "requires": {
        "rc": "^1.2.8"
      }
    },
    "registry-url": {
      "version": "5.1.0",
      "resolved": "https://registry.npmjs.org/registry-url/-/registry-url-5.1.0.tgz",
      "integrity": "sha512-8acYXXTI0AkQv6RAOjE3vOaIXZkT9wo4LOFbBKYQEEnnMNBpKqdUrI6S4NT0KPIo/WVvJ5tE/X5LF/TQUf0ekw==",
      "requires": {
        "rc": "^1.2.8"
      }
    },
    "regjsgen": {
      "version": "0.5.2",
      "resolved": "https://registry.npmjs.org/regjsgen/-/regjsgen-0.5.2.tgz",
      "integrity": "sha512-OFFT3MfrH90xIW8OOSyUrk6QHD5E9JOTeGodiJeBS3J6IwlgzJMNE/1bZklWz5oTg+9dCMyEetclvCVXOPoN3A==",
      "dev": true
    },
    "regjsparser": {
      "version": "0.7.0",
      "resolved": "https://registry.npmjs.org/regjsparser/-/regjsparser-0.7.0.tgz",
      "integrity": "sha512-A4pcaORqmNMDVwUjWoTzuhwMGpP+NykpfqAsEgI1FSH/EzC7lrN5TMd+kN8YCovX+jMpu8eaqXgXPCa0g8FQNQ==",
      "dev": true,
      "requires": {
        "jsesc": "~0.5.0"
      },
      "dependencies": {
        "jsesc": {
          "version": "0.5.0",
          "resolved": "https://registry.npmjs.org/jsesc/-/jsesc-0.5.0.tgz",
          "integrity": "sha1-597mbjXW/Bb3EP6R1c9p9w8IkR0=",
          "dev": true
        }
      }
    },
    "require-directory": {
      "version": "2.1.1",
      "resolved": "https://registry.npmjs.org/require-directory/-/require-directory-2.1.1.tgz",
      "integrity": "sha1-jGStX9MNqxyXbiNE/+f3kqam30I="
    },
    "require-from-string": {
      "version": "2.0.2",
      "resolved": "https://registry.npmjs.org/require-from-string/-/require-from-string-2.0.2.tgz",
      "integrity": "sha512-Xf0nWe6RseziFMu+Ap9biiUbmplq6S9/p+7w7YXP/JBHhrUDDUhwa+vANyubuqfZWTveU//DYVGsDG7RKL/vEw==",
      "dev": true
    },
    "requires-port": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/requires-port/-/requires-port-1.0.0.tgz",
      "integrity": "sha1-kl0mAdOaxIXgkc8NpcbmlNw9yv8=",
      "dev": true
    },
    "resolve": {
      "version": "1.20.0",
      "resolved": "https://registry.npmjs.org/resolve/-/resolve-1.20.0.tgz",
      "integrity": "sha512-wENBPt4ySzg4ybFQW2TT1zMQucPK95HSh/nq2CFTZVOGut2+pQvSsgtda4d26YrYcr067wjbmzOG8byDPBX63A==",
      "dev": true,
      "requires": {
        "is-core-module": "^2.2.0",
        "path-parse": "^1.0.6"
      }
    },
    "resolve-from": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/resolve-from/-/resolve-from-5.0.0.tgz",
      "integrity": "sha512-qYg9KP24dD5qka9J47d0aVky0N+b4fTU89LN9iDnjB5waksiC49rvMB0PrUJQGoTmH50XPiqOvAjDfaijGxYZw==",
      "dev": true
    },
    "resolve-url-loader": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/resolve-url-loader/-/resolve-url-loader-4.0.0.tgz",
      "integrity": "sha512-05VEMczVREcbtT7Bz+C+96eUO5HDNvdthIiMB34t7FcF8ehcu4wC0sSgPUubs3XW2Q3CNLJk/BJrCU9wVRymiA==",
      "dev": true,
      "requires": {
        "adjust-sourcemap-loader": "^4.0.0",
        "convert-source-map": "^1.7.0",
        "loader-utils": "^2.0.0",
        "postcss": "^7.0.35",
        "source-map": "0.6.1"
      },
      "dependencies": {
        "loader-utils": {
          "version": "2.0.2",
          "resolved": "https://registry.npmjs.org/loader-utils/-/loader-utils-2.0.2.tgz",
          "integrity": "sha512-TM57VeHptv569d/GKh6TAYdzKblwDNiumOdkFnejjD0XwTH87K90w3O7AiJRqdQoXygvi1VQTJTLGhJl7WqA7A==",
          "dev": true,
          "requires": {
            "big.js": "^5.2.2",
            "emojis-list": "^3.0.0",
            "json5": "^2.1.2"
          }
        },
        "picocolors": {
          "version": "0.2.1",
          "resolved": "https://registry.npmjs.org/picocolors/-/picocolors-0.2.1.tgz",
          "integrity": "sha512-cMlDqaLEqfSaW8Z7N5Jw+lyIW869EzT73/F5lhtY9cLGoVxSXznfgfXMO0Z5K0o0Q2TkTXq+0KFsdnSe3jDViA==",
          "dev": true
        },
        "postcss": {
          "version": "7.0.39",
          "resolved": "https://registry.npmjs.org/postcss/-/postcss-7.0.39.tgz",
          "integrity": "sha512-yioayjNbHn6z1/Bywyb2Y4s3yvDAeXGOyxqD+LnVOinq6Mdmd++SW2wUNVzavyyHxd6+DxzWGIuosg6P1Rj8uA==",
          "dev": true,
          "requires": {
            "picocolors": "^0.2.1",
            "source-map": "^0.6.1"
          }
        },
        "source-map": {
          "version": "0.6.1",
          "resolved": "https://registry.npmjs.org/source-map/-/source-map-0.6.1.tgz",
          "integrity": "sha512-UjgapumWlbMhkBgzT7Ykc5YXUT46F0iKu8SGXq0bcwP5dz/h0Plj6enJqjz1Zbq2l5WaqYnrVbwWOWMyF3F47g==",
          "dev": true
        }
      }
    },
    "responselike": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/responselike/-/responselike-1.0.2.tgz",
      "integrity": "sha1-kYcg7ztjHFZCvgaPFa3lpG9Loec=",
      "requires": {
        "lowercase-keys": "^1.0.0"
      }
    },
    "restore-cursor": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/restore-cursor/-/restore-cursor-3.1.0.tgz",
      "integrity": "sha512-l+sSefzHpj5qimhFSE5a8nufZYAM3sBSVMAPtYkmC+4EH2anSGaEMXSD0izRQbu9nfyQ9y5JrVmp7E8oZrUjvA==",
      "dev": true,
      "requires": {
        "onetime": "^5.1.0",
        "signal-exit": "^3.0.2"
      }
    },
    "retry": {
      "version": "0.12.0",
      "resolved": "https://registry.npmjs.org/retry/-/retry-0.12.0.tgz",
      "integrity": "sha1-G0KmJmoh8HQh0bC1S33BZ7AcATs=",
      "dev": true
    },
    "reusify": {
      "version": "1.0.4",
      "resolved": "https://registry.npmjs.org/reusify/-/reusify-1.0.4.tgz",
      "integrity": "sha512-U9nH88a3fc/ekCF1l0/UP1IosiuIjyTh7hBvXVMHYgVcfGvt897Xguj2UOLDeI5BG2m7/uwyaLVT6fbtCwTyzw==",
      "dev": true
    },
    "rfdc": {
      "version": "1.3.0",
      "resolved": "https://registry.npmjs.org/rfdc/-/rfdc-1.3.0.tgz",
      "integrity": "sha512-V2hovdzFbOi77/WajaSMXk2OLm+xNIeQdMMuB7icj7bk6zi2F8GGAxigcnDFpJHbNyNcgyJDiP+8nOrY5cZGrA==",
      "dev": true
    },
    "rimraf": {
      "version": "3.0.2",
      "resolved": "https://registry.npmjs.org/rimraf/-/rimraf-3.0.2.tgz",
      "integrity": "sha512-JZkJMZkAGFFPP2YqXZXPbMlMBgsxzE8ILs4lMIX/2o0L9UBw9O/Y3o6wFw/i9YLapcUJWwqbi3kdxIPdC62TIA==",
      "dev": true,
      "requires": {
        "glob": "^7.1.3"
      }
    },
    "run-async": {
      "version": "2.4.1",
      "resolved": "https://registry.npmjs.org/run-async/-/run-async-2.4.1.tgz",
      "integrity": "sha512-tvVnVv01b8c1RrA6Ep7JkStj85Guv/YrMcwqYQnwjsAS2cTmmPGBBjAjpCW7RrSodNSoE2/qg9O4bceNvUuDgQ==",
      "dev": true
    },
    "run-parallel": {
      "version": "1.2.0",
      "resolved": "https://registry.npmjs.org/run-parallel/-/run-parallel-1.2.0.tgz",
      "integrity": "sha512-5l4VyZR86LZ/lDxZTR6jqL8AFE2S0IFLMP26AbjsLVADxHdhB/c0GUsH+y39UfCi3dzz8OlQuPmnaJOMoDHQBA==",
      "dev": true,
      "requires": {
        "queue-microtask": "^1.2.2"
      }
    },
    "rxjs": {
      "version": "7.4.0",
      "resolved": "https://registry.npmjs.org/rxjs/-/rxjs-7.4.0.tgz",
      "integrity": "sha512-7SQDi7xeTMCJpqViXh8gL/lebcwlp3d831F05+9B44A4B0WfsEwUQHR64gsH1kvJ+Ep/J9K2+n1hVl1CsGN23w==",
      "requires": {
        "tslib": "~2.1.0"
      },
      "dependencies": {
        "tslib": {
          "version": "2.1.0",
          "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.1.0.tgz",
          "integrity": "sha512-hcVC3wYEziELGGmEEXue7D75zbwIIVUMWAVbHItGPx0ziyXxrOMQx4rQEVEV45Ut/1IotuEvwqPopzIOkDMf0A=="
        }
      }
    },
    "safe-buffer": {
      "version": "5.1.2",
      "resolved": "https://registry.npmjs.org/safe-buffer/-/safe-buffer-5.1.2.tgz",
      "integrity": "sha512-Gd2UZBJDkXlY7GbJxfsE8/nvKkUEU1G38c1siN6QP6a9PT9MmHB8GnpscSmMJSoF8LOIrt8ud/wPtojys4G6+g=="
    },
    "safer-buffer": {
      "version": "2.1.2",
      "resolved": "https://registry.npmjs.org/safer-buffer/-/safer-buffer-2.1.2.tgz",
      "integrity": "sha512-YZo3K82SD7Riyi0E1EQPojLz7kpepnSQI9IyPbHHg1XXXevb5dJI7tpyN2ADxGcQbHG7vcyRHk0cbwqcQriUtg=="
    },
    "sass": {
      "version": "1.44.0",
      "resolved": "https://registry.npmjs.org/sass/-/sass-1.44.0.tgz",
      "integrity": "sha512-0hLREbHFXGQqls/K8X+koeP+ogFRPF4ZqetVB19b7Cst9Er8cOR0rc6RU7MaI4W1JmUShd1BPgPoeqmmgMMYFw==",
      "dev": true,
      "requires": {
        "chokidar": ">=3.0.0 <4.0.0",
        "immutable": "^4.0.0"
      }
    },
    "sass-loader": {
      "version": "12.4.0",
      "resolved": "https://registry.npmjs.org/sass-loader/-/sass-loader-12.4.0.tgz",
      "integrity": "sha512-7xN+8khDIzym1oL9XyS6zP6Ges+Bo2B2xbPrjdMHEYyV3AQYhd/wXeru++3ODHF0zMjYmVadblSKrPrjEkL8mg==",
      "dev": true,
      "requires": {
        "klona": "^2.0.4",
        "neo-async": "^2.6.2"
      }
    },
    "sax": {
      "version": "1.2.4",
      "resolved": "https://registry.npmjs.org/sax/-/sax-1.2.4.tgz",
      "integrity": "sha512-NqVDv9TpANUjFm0N8uM5GxL36UgKi9/atZw+x7YFnQ8ckwFGKrl4xX4yWtrey3UJm5nP1kUbnYgLopqWNSRhWw==",
      "dev": true
    },
    "schema-utils": {
      "version": "2.7.1",
      "resolved": "https://registry.npmjs.org/schema-utils/-/schema-utils-2.7.1.tgz",
      "integrity": "sha512-SHiNtMOUGWBQJwzISiVYKu82GiV4QYGePp3odlY1tuKO7gPtphAT5R/py0fA6xtbgLL/RvtJZnU9b8s0F1q0Xg==",
      "dev": true,
      "requires": {
        "@types/json-schema": "^7.0.5",
        "ajv": "^6.12.4",
        "ajv-keywords": "^3.5.2"
      },
      "dependencies": {
        "ajv": {
          "version": "6.12.6",
          "resolved": "https://registry.npmjs.org/ajv/-/ajv-6.12.6.tgz",
          "integrity": "sha512-j3fVLgvTo527anyYyJOGTYJbG+vnnQYvE0m5mmkc1TK+nxAppkCLMIL0aZ4dblVCNoGShhm+kzE4ZUykBoMg4g==",
          "dev": true,
          "requires": {
            "fast-deep-equal": "^3.1.1",
            "fast-json-stable-stringify": "^2.0.0",
            "json-schema-traverse": "^0.4.1",
            "uri-js": "^4.2.2"
          }
        },
        "ajv-keywords": {
          "version": "3.5.2",
          "resolved": "https://registry.npmjs.org/ajv-keywords/-/ajv-keywords-3.5.2.tgz",
          "integrity": "sha512-5p6WTN0DdTGVQk6VjcEju19IgaHudalcfabD7yhDGeA6bcQnmL+CpveLJq/3hvfwd1aof6L386Ougkx6RfyMIQ==",
          "dev": true,
          "requires": {}
        },
        "json-schema-traverse": {
          "version": "0.4.1",
          "resolved": "https://registry.npmjs.org/json-schema-traverse/-/json-schema-traverse-0.4.1.tgz",
          "integrity": "sha512-xbbCH5dCYU5T8LcEhhuh7HJ88HXuW3qsI3Y0zOZFKfZEHcpWiHU/Jxzk629Brsab/mMiHQti9wMP+845RPe3Vg==",
          "dev": true
        }
      }
    },
    "select-hose": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/select-hose/-/select-hose-2.0.0.tgz",
      "integrity": "sha1-Yl2GWPhlr0Psliv8N2o3NZpJlMo=",
      "dev": true
    },
    "selfsigned": {
      "version": "1.10.14",
      "resolved": "https://registry.npmjs.org/selfsigned/-/selfsigned-1.10.14.tgz",
      "integrity": "sha512-lkjaiAye+wBZDCBsu5BGi0XiLRxeUlsGod5ZP924CRSEoGuZAw/f7y9RKu28rwTfiHVhdavhB0qH0INV6P1lEA==",
      "dev": true,
      "requires": {
        "node-forge": "^0.10.0"
      }
    },
    "semver": {
      "version": "7.3.5",
      "resolved": "https://registry.npmjs.org/semver/-/semver-7.3.5.tgz",
      "integrity": "sha512-PoeGJYh8HK4BTO/a9Tf6ZG3veo/A7ZVsYrSA6J8ny9nb3B1VrpkuN+z9OE5wfE5p6H4LchYZsegiQgbJD94ZFQ==",
      "requires": {
        "lru-cache": "^6.0.0"
      }
    },
    "semver-compare": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/semver-compare/-/semver-compare-1.0.0.tgz",
      "integrity": "sha1-De4hahyUGrN+nvsXiPavxf9VN/w="
    },
    "semver-diff": {
      "version": "3.1.1",
      "resolved": "https://registry.npmjs.org/semver-diff/-/semver-diff-3.1.1.tgz",
      "integrity": "sha512-GX0Ix/CJcHyB8c4ykpHGIAvLyOwOobtM/8d+TQkAd81/bEjgPHrfba41Vpesr7jX/t8Uh+R3EX9eAS5be+jQYg==",
      "requires": {
        "semver": "^6.3.0"
      },
      "dependencies": {
        "semver": {
          "version": "6.3.0",
          "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.0.tgz",
          "integrity": "sha512-b39TBaTSfV6yBrapU89p5fKekE2m/NwnDocOVruQFS1/veMgdzuPcnOM34M6CwxW8jH/lxEa5rBoDeUwu5HHTw=="
        }
      }
    },
    "send": {
      "version": "0.17.2",
      "resolved": "https://registry.npmjs.org/send/-/send-0.17.2.tgz",
      "integrity": "sha512-UJYB6wFSJE3G00nEivR5rgWp8c2xXvJ3OPWPhmuteU0IKj8nKbG3DrjiOmLwpnHGYWAVwA69zmTm++YG0Hmwww==",
      "requires": {
        "debug": "2.6.9",
        "depd": "~1.1.2",
        "destroy": "~1.0.4",
        "encodeurl": "~1.0.2",
        "escape-html": "~1.0.3",
        "etag": "~1.8.1",
        "fresh": "0.5.2",
        "http-errors": "1.8.1",
        "mime": "1.6.0",
        "ms": "2.1.3",
        "on-finished": "~2.3.0",
        "range-parser": "~1.2.1",
        "statuses": "~1.5.0"
      },
      "dependencies": {
        "debug": {
          "version": "2.6.9",
          "resolved": "https://registry.npmjs.org/debug/-/debug-2.6.9.tgz",
          "integrity": "sha512-bC7ElrdJaJnPbAP+1EotYvqZsb3ecl5wi6Bfi6BJTUcNowp6cvspg0jXznRTKDjm/E7AdgFBVeAPVMNcKGsHMA==",
          "requires": {
            "ms": "2.0.0"
          },
          "dependencies": {
            "ms": {
              "version": "2.0.0",
              "resolved": "https://registry.npmjs.org/ms/-/ms-2.0.0.tgz",
              "integrity": "sha1-VgiurfwAvmwpAd9fmGF4jeDVl8g="
            }
          }
        },
        "mime": {
          "version": "1.6.0",
          "resolved": "https://registry.npmjs.org/mime/-/mime-1.6.0.tgz",
          "integrity": "sha512-x0Vn8spI+wuJ1O6S7gnbaQg8Pxh4NNHb7KSINmEWKiPE4RKOplvijn+NkmYmmRgP68mc70j2EbeTFRsrswaQeg=="
        },
        "ms": {
          "version": "2.1.3",
          "resolved": "https://registry.npmjs.org/ms/-/ms-2.1.3.tgz",
          "integrity": "sha512-6FlzubTLZG3J2a/NVCAleEhjzq5oxgHyaCU9yYXvcLsvoVaHJq/s5xXI6/XXP6tz7R9xAOtHnSO/tXtF3WRTlA=="
        }
      }
    },
    "serialize-javascript": {
      "version": "6.0.0",
      "resolved": "https://registry.npmjs.org/serialize-javascript/-/serialize-javascript-6.0.0.tgz",
      "integrity": "sha512-Qr3TosvguFt8ePWqsvRfrKyQXIiW+nGbYpy8XK24NQHE83caxWt+mIymTT19DGFbNWNLfEwsrkSmN64lVWB9ag==",
      "dev": true,
      "requires": {
        "randombytes": "^2.1.0"
      }
    },
    "serve-index": {
      "version": "1.9.1",
      "resolved": "https://registry.npmjs.org/serve-index/-/serve-index-1.9.1.tgz",
      "integrity": "sha1-03aNabHn2C5c4FD/9bRTvqEqkjk=",
      "dev": true,
      "requires": {
        "accepts": "~1.3.4",
        "batch": "0.6.1",
        "debug": "2.6.9",
        "escape-html": "~1.0.3",
        "http-errors": "~1.6.2",
        "mime-types": "~2.1.17",
        "parseurl": "~1.3.2"
      },
      "dependencies": {
        "debug": {
          "version": "2.6.9",
          "resolved": "https://registry.npmjs.org/debug/-/debug-2.6.9.tgz",
          "integrity": "sha512-bC7ElrdJaJnPbAP+1EotYvqZsb3ecl5wi6Bfi6BJTUcNowp6cvspg0jXznRTKDjm/E7AdgFBVeAPVMNcKGsHMA==",
          "dev": true,
          "requires": {
            "ms": "2.0.0"
          }
        },
        "http-errors": {
          "version": "1.6.3",
          "resolved": "https://registry.npmjs.org/http-errors/-/http-errors-1.6.3.tgz",
          "integrity": "sha1-i1VoC7S+KDoLW/TqLjhYC+HZMg0=",
          "dev": true,
          "requires": {
            "depd": "~1.1.2",
            "inherits": "2.0.3",
            "setprototypeof": "1.1.0",
            "statuses": ">= 1.4.0 < 2"
          }
        },
        "inherits": {
          "version": "2.0.3",
          "resolved": "https://registry.npmjs.org/inherits/-/inherits-2.0.3.tgz",
          "integrity": "sha1-Yzwsg+PaQqUC9SRmAiSA9CCCYd4=",
          "dev": true
        },
        "ms": {
          "version": "2.0.0",
          "resolved": "https://registry.npmjs.org/ms/-/ms-2.0.0.tgz",
          "integrity": "sha1-VgiurfwAvmwpAd9fmGF4jeDVl8g=",
          "dev": true
        },
        "setprototypeof": {
          "version": "1.1.0",
          "resolved": "https://registry.npmjs.org/setprototypeof/-/setprototypeof-1.1.0.tgz",
          "integrity": "sha512-BvE/TwpZX4FXExxOxZyRGQQv651MSwmWKZGqvmPcRIjDqWub67kTKuIMx43cZZrS/cBBzwBcNDWoFxt2XEFIpQ==",
          "dev": true
        }
      }
    },
    "serve-static": {
      "version": "1.14.2",
      "resolved": "https://registry.npmjs.org/serve-static/-/serve-static-1.14.2.tgz",
      "integrity": "sha512-+TMNA9AFxUEGuC0z2mevogSnn9MXKb4fa7ngeRMJaaGv8vTwnIEkKi+QGvPt33HSnf8pRS+WGM0EbMtCJLKMBQ==",
      "requires": {
        "encodeurl": "~1.0.2",
        "escape-html": "~1.0.3",
        "parseurl": "~1.3.3",
        "send": "0.17.2"
      }
    },
    "server-destroy": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/server-destroy/-/server-destroy-1.0.1.tgz",
      "integrity": "sha1-8Tv5KOQrnD55OD5hzDmYtdFObN0="
    },
    "set-blocking": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/set-blocking/-/set-blocking-2.0.0.tgz",
      "integrity": "sha1-BF+XgtARrppoA93TgrJDkrPYkPc=",
      "dev": true
    },
    "setprototypeof": {
      "version": "1.2.0",
      "resolved": "https://registry.npmjs.org/setprototypeof/-/setprototypeof-1.2.0.tgz",
      "integrity": "sha512-E5LDX7Wrp85Kil5bhZv46j8jOeboKq5JMmYM3gVGdGH8xFpPWXUMsNrlODCrkoxMEeNi/XZIwuRvY4XNwYMJpw=="
    },
    "shallow-clone": {
      "version": "3.0.1",
      "resolved": "https://registry.npmjs.org/shallow-clone/-/shallow-clone-3.0.1.tgz",
      "integrity": "sha512-/6KqX+GVUdqPuPPd2LxDDxzX6CAbjJehAAOKlNpqqUpAqPM6HeL8f+o3a+JsyGjn2lv0WY8UsTgUJjU9Ok55NA==",
      "dev": true,
      "requires": {
        "kind-of": "^6.0.2"
      }
    },
    "shebang-command": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/shebang-command/-/shebang-command-2.0.0.tgz",
      "integrity": "sha512-kHxr2zZpYtdmrN1qDjrrX/Z1rR1kG8Dx+gkpK1G4eXmvXswmcE1hTWBWYUzlraYw1/yZp6YuDY77YtvbN0dmDA==",
      "dev": true,
      "requires": {
        "shebang-regex": "^3.0.0"
      }
    },
    "shebang-regex": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/shebang-regex/-/shebang-regex-3.0.0.tgz",
      "integrity": "sha512-7++dFhtcx3353uBaq8DDR4NuxBetBzC7ZQOhmTQInHEd6bSrXdiEyzCvG07Z44UYdLShWUyXt5M/yhz8ekcb1A==",
      "dev": true
    },
    "signal-exit": {
      "version": "3.0.6",
      "resolved": "https://registry.npmjs.org/signal-exit/-/signal-exit-3.0.6.tgz",
      "integrity": "sha512-sDl4qMFpijcGw22U5w63KmD3cZJfBuFlVNbVMKje2keoKML7X2UzWbc4XrmEbDwg0NXJc3yv4/ox7b+JWb57kQ=="
    },
    "slash": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/slash/-/slash-4.0.0.tgz",
      "integrity": "sha512-3dOsAHXXUkQTpOYcoAxLIorMTp4gIQr5IW3iVb7A7lFIp0VHhnynm9izx6TssdrIcVIESAlVjtnO2K8bg+Coew==",
      "dev": true
    },
    "smart-buffer": {
      "version": "4.2.0",
      "resolved": "https://registry.npmjs.org/smart-buffer/-/smart-buffer-4.2.0.tgz",
      "integrity": "sha512-94hK0Hh8rPqQl2xXc3HsaBoOXKV20MToPkcXvwbISWLEs+64sBq5kFgn2kJDHb1Pry9yrP0dxrCI9RRci7RXKg==",
      "dev": true
    },
    "socket.io": {
      "version": "4.4.1",
      "resolved": "https://registry.npmjs.org/socket.io/-/socket.io-4.4.1.tgz",
      "integrity": "sha512-s04vrBswdQBUmuWJuuNTmXUVJhP0cVky8bBDhdkf8y0Ptsu7fKU2LuLbts9g+pdmAdyMMn8F/9Mf1/wbtUN0fg==",
      "dev": true,
      "requires": {
        "accepts": "~1.3.4",
        "base64id": "~2.0.0",
        "debug": "~4.3.2",
        "engine.io": "~6.1.0",
        "socket.io-adapter": "~2.3.3",
        "socket.io-parser": "~4.0.4"
      }
    },
    "socket.io-adapter": {
      "version": "2.3.3",
      "resolved": "https://registry.npmjs.org/socket.io-adapter/-/socket.io-adapter-2.3.3.tgz",
      "integrity": "sha512-Qd/iwn3VskrpNO60BeRyCyr8ZWw9CPZyitW4AQwmRZ8zCiyDiL+znRnWX6tDHXnWn1sJrM1+b6Mn6wEDJJ4aYQ==",
      "dev": true
    },
    "socket.io-parser": {
      "version": "4.0.4",
      "resolved": "https://registry.npmjs.org/socket.io-parser/-/socket.io-parser-4.0.4.tgz",
      "integrity": "sha512-t+b0SS+IxG7Rxzda2EVvyBZbvFPBCjJoyHuE0P//7OAsN23GItzDRdWa6ALxZI/8R5ygK7jAR6t028/z+7295g==",
      "dev": true,
      "requires": {
        "@types/component-emitter": "^1.2.10",
        "component-emitter": "~1.3.0",
        "debug": "~4.3.1"
      }
    },
    "sockjs": {
      "version": "0.3.24",
      "resolved": "https://registry.npmjs.org/sockjs/-/sockjs-0.3.24.tgz",
      "integrity": "sha512-GJgLTZ7vYb/JtPSSZ10hsOYIvEYsjbNU+zPdIHcUaWVNUEPivzxku31865sSSud0Da0W4lEeOPlmw93zLQchuQ==",
      "dev": true,
      "requires": {
        "faye-websocket": "^0.11.3",
        "uuid": "^8.3.2",
        "websocket-driver": "^0.7.4"
      }
    },
    "socks": {
      "version": "2.6.1",
      "resolved": "https://registry.npmjs.org/socks/-/socks-2.6.1.tgz",
      "integrity": "sha512-kLQ9N5ucj8uIcxrDwjm0Jsqk06xdpBjGNQtpXy4Q8/QY2k+fY7nZH8CARy+hkbG+SGAovmzzuauCpBlb8FrnBA==",
      "dev": true,
      "requires": {
        "ip": "^1.1.5",
        "smart-buffer": "^4.1.0"
      }
    },
    "socks-proxy-agent": {
      "version": "6.1.1",
      "resolved": "https://registry.npmjs.org/socks-proxy-agent/-/socks-proxy-agent-6.1.1.tgz",
      "integrity": "sha512-t8J0kG3csjA4g6FTbsMOWws+7R7vuRC8aQ/wy3/1OWmsgwA68zs/+cExQ0koSitUDXqhufF/YJr9wtNMZHw5Ew==",
      "dev": true,
      "requires": {
        "agent-base": "^6.0.2",
        "debug": "^4.3.1",
        "socks": "^2.6.1"
      }
    },
    "source-map": {
      "version": "0.7.3",
      "resolved": "https://registry.npmjs.org/source-map/-/source-map-0.7.3.tgz",
      "integrity": "sha512-CkCj6giN3S+n9qrYiBTX5gystlENnRW5jZeNLHpe6aue+SrHcG5VYwujhW9s4dY31mEGsxBDrHR6oI69fTXsaQ==",
      "dev": true
    },
    "source-map-js": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/source-map-js/-/source-map-js-1.0.2.tgz",
      "integrity": "sha512-R0XvVJ9WusLiqTCEiGCmICCMplcCkIwwR11mOSD9CR5u+IXYdiseeEuXCVAjS54zqwkLcPNnmU4OeJ6tUrWhDw==",
      "dev": true
    },
    "source-map-loader": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/source-map-loader/-/source-map-loader-3.0.0.tgz",
      "integrity": "sha512-GKGWqWvYr04M7tn8dryIWvb0s8YM41z82iQv01yBtIylgxax0CwvSy6gc2Y02iuXwEfGWRlMicH0nvms9UZphw==",
      "dev": true,
      "requires": {
        "abab": "^2.0.5",
        "iconv-lite": "^0.6.2",
        "source-map-js": "^0.6.2"
      },
      "dependencies": {
        "iconv-lite": {
          "version": "0.6.3",
          "resolved": "https://registry.npmjs.org/iconv-lite/-/iconv-lite-0.6.3.tgz",
          "integrity": "sha512-4fCk79wshMdzMp2rH06qWrJE4iolqLhCUH+OiuIgU++RB0+94NlDL81atO7GX55uUKueo0txHNtvEyI6D7WdMw==",
          "dev": true,
          "requires": {
            "safer-buffer": ">= 2.1.2 < 3.0.0"
          }
        },
        "source-map-js": {
          "version": "0.6.2",
          "resolved": "https://registry.npmjs.org/source-map-js/-/source-map-js-0.6.2.tgz",
          "integrity": "sha512-/3GptzWzu0+0MBQFrDKzw/DvvMTUORvgY6k6jd/VS6iCR4RDTKWH6v6WPwQoUO8667uQEf9Oe38DxAYWY5F/Ug==",
          "dev": true
        }
      }
    },
    "source-map-resolve": {
      "version": "0.6.0",
      "resolved": "https://registry.npmjs.org/source-map-resolve/-/source-map-resolve-0.6.0.tgz",
      "integrity": "sha512-KXBr9d/fO/bWo97NXsPIAW1bFSBOuCnjbNTBMO7N59hsv5i9yzRDfcYwwt0l04+VqnKC+EwzvJZIP/qkuMgR/w==",
      "dev": true,
      "requires": {
        "atob": "^2.1.2",
        "decode-uri-component": "^0.2.0"
      }
    },
    "source-map-support": {
      "version": "0.5.21",
      "resolved": "https://registry.npmjs.org/source-map-support/-/source-map-support-0.5.21.tgz",
      "integrity": "sha512-uBHU3L3czsIyYXKX88fdrGovxdSCoTGDRZ6SYXtSRxLZUzHg5P/66Ht6uoUlHu9EZod+inXhKo3qQgwXUT/y1w==",
      "dev": true,
      "requires": {
        "buffer-from": "^1.0.0",
        "source-map": "^0.6.0"
      },
      "dependencies": {
        "source-map": {
          "version": "0.6.1",
          "resolved": "https://registry.npmjs.org/source-map/-/source-map-0.6.1.tgz",
          "integrity": "sha512-UjgapumWlbMhkBgzT7Ykc5YXUT46F0iKu8SGXq0bcwP5dz/h0Plj6enJqjz1Zbq2l5WaqYnrVbwWOWMyF3F47g==",
          "dev": true
        }
      }
    },
    "sourcemap-codec": {
      "version": "1.4.8",
      "resolved": "https://registry.npmjs.org/sourcemap-codec/-/sourcemap-codec-1.4.8.tgz",
      "integrity": "sha512-9NykojV5Uih4lgo5So5dtw+f0JgJX30KCNI8gwhz2J9A15wD0Ml6tjHKwf6fTSa6fAdVBdZeNOs9eJ71qCk8vA==",
      "dev": true
    },
    "spdy": {
      "version": "4.0.2",
      "resolved": "https://registry.npmjs.org/spdy/-/spdy-4.0.2.tgz",
      "integrity": "sha512-r46gZQZQV+Kl9oItvl1JZZqJKGr+oEkB08A6BzkiR7593/7IbtuncXHd2YoYeTsG4157ZssMu9KYvUHLcjcDoA==",
      "dev": true,
      "requires": {
        "debug": "^4.1.0",
        "handle-thing": "^2.0.0",
        "http-deceiver": "^1.2.7",
        "select-hose": "^2.0.0",
        "spdy-transport": "^3.0.0"
      }
    },
    "spdy-transport": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/spdy-transport/-/spdy-transport-3.0.0.tgz",
      "integrity": "sha512-hsLVFE5SjA6TCisWeJXFKniGGOpBgMLmerfO2aCyCU5s7nJ/rpAepqmFifv/GCbSbueEeAJJnmSQ2rKC/g8Fcw==",
      "dev": true,
      "requires": {
        "debug": "^4.1.0",
        "detect-node": "^2.0.4",
        "hpack.js": "^2.1.6",
        "obuf": "^1.1.2",
        "readable-stream": "^3.0.6",
        "wbuf": "^1.7.3"
      }
    },
    "sprintf-js": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/sprintf-js/-/sprintf-js-1.0.3.tgz",
      "integrity": "sha1-BOaSb2YolTVPPdAVIDYzuFcpfiw=",
      "dev": true
    },
    "ssri": {
      "version": "8.0.1",
      "resolved": "https://registry.npmjs.org/ssri/-/ssri-8.0.1.tgz",
      "integrity": "sha512-97qShzy1AiyxvPNIkLWoGua7xoQzzPjQ0HAH4B0rWKo7SZ6USuPcrUiAFrws0UH8RrbWmgq3LMTObhPIHbbBeQ==",
      "dev": true,
      "requires": {
        "minipass": "^3.1.1"
      }
    },
    "statuses": {
      "version": "1.5.0",
      "resolved": "https://registry.npmjs.org/statuses/-/statuses-1.5.0.tgz",
      "integrity": "sha1-Fhx9rBd2Wf2YEfQ3cfqZOBR4Yow="
    },
    "steno": {
      "version": "0.4.4",
      "resolved": "https://registry.npmjs.org/steno/-/steno-0.4.4.tgz",
      "integrity": "sha1-BxEFvfwobmYVwEA8J+nXtdy4Vcs=",
      "requires": {
        "graceful-fs": "^4.1.3"
      }
    },
    "streamroller": {
      "version": "3.0.2",
      "resolved": "https://registry.npmjs.org/streamroller/-/streamroller-3.0.2.tgz",
      "integrity": "sha512-ur6y5S5dopOaRXBuRIZ1u6GC5bcEXHRZKgfBjfCglMhmIf+roVCECjvkEYzNQOXIN2/JPnkMPW/8B3CZoKaEPA==",
      "dev": true,
      "requires": {
        "date-format": "^4.0.3",
        "debug": "^4.1.1",
        "fs-extra": "^10.0.0"
      }
    },
    "string_decoder": {
      "version": "1.3.0",
      "resolved": "https://registry.npmjs.org/string_decoder/-/string_decoder-1.3.0.tgz",
      "integrity": "sha512-hkRX8U1WjJFd8LsDJ2yQ/wWWxaopEsABU1XfkM8A+j0+85JAGppt16cr1Whg6KIbb4okU6Mql6BOj+uup/wKeA==",
      "dev": true,
      "requires": {
        "safe-buffer": "~5.2.0"
      },
      "dependencies": {
        "safe-buffer": {
          "version": "5.2.1",
          "resolved": "https://registry.npmjs.org/safe-buffer/-/safe-buffer-5.2.1.tgz",
          "integrity": "sha512-rp3So07KcdmmKbGvgaNxQSJr7bGVSVk5S9Eq1F+ppbRo70+YeaDxkw5Dd8NPN+GD6bjnYm2VuPuCXmpuYvmCXQ==",
          "dev": true
        }
      }
    },
    "string-width": {
      "version": "4.2.3",
      "resolved": "https://registry.npmjs.org/string-width/-/string-width-4.2.3.tgz",
      "integrity": "sha512-wKyQRQpjJ0sIp62ErSZdGsjMJWsap5oRNihHhu6G7JVO/9jIB6UyevL+tXuOqrng8j/cxKTWyWUwvSTriiZz/g==",
      "requires": {
        "emoji-regex": "^8.0.0",
        "is-fullwidth-code-point": "^3.0.0",
        "strip-ansi": "^6.0.1"
      }
    },
    "strip-ansi": {
      "version": "6.0.1",
      "resolved": "https://registry.npmjs.org/strip-ansi/-/strip-ansi-6.0.1.tgz",
      "integrity": "sha512-Y38VPSHcqkFrCpFnQ9vuSXmquuv5oXOKpGeT6aGrr3o3Gc9AlVa6JBfUSOCnbxGGZF+/0ooI7KrPuUSztUdU5A==",
      "requires": {
        "ansi-regex": "^5.0.1"
      }
    },
    "strip-final-newline": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/strip-final-newline/-/strip-final-newline-2.0.0.tgz",
      "integrity": "sha512-BrpvfNAE3dcvq7ll3xVumzjKjZQ5tI1sEUIKr3Uoks0XUl45St3FlatVqef9prk4jRDzhW6WZg+3bk93y6pLjA==",
      "dev": true
    },
    "strip-json-comments": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/strip-json-comments/-/strip-json-comments-2.0.1.tgz",
      "integrity": "sha1-PFMZQukIwml8DsNEhYwobHygpgo="
    },
    "stylus": {
      "version": "0.55.0",
      "resolved": "https://registry.npmjs.org/stylus/-/stylus-0.55.0.tgz",
      "integrity": "sha512-MuzIIVRSbc8XxHH7FjkvWqkIcr1BvoMZoR/oFuAJDlh7VSaNJzrB4uJ38GRQa+mWjLXODAMzeDe0xi9GYbGwnw==",
      "dev": true,
      "requires": {
        "css": "^3.0.0",
        "debug": "~3.1.0",
        "glob": "^7.1.6",
        "mkdirp": "~1.0.4",
        "safer-buffer": "^2.1.2",
        "sax": "~1.2.4",
        "semver": "^6.3.0",
        "source-map": "^0.7.3"
      },
      "dependencies": {
        "debug": {
          "version": "3.1.0",
          "resolved": "https://registry.npmjs.org/debug/-/debug-3.1.0.tgz",
          "integrity": "sha512-OX8XqP7/1a9cqkxYw2yXss15f26NKWBpDXQd0/uK/KPqdQhxbPa994hnzjcE2VqQpDslf55723cKPUOGSmMY3g==",
          "dev": true,
          "requires": {
            "ms": "2.0.0"
          }
        },
        "ms": {
          "version": "2.0.0",
          "resolved": "https://registry.npmjs.org/ms/-/ms-2.0.0.tgz",
          "integrity": "sha1-VgiurfwAvmwpAd9fmGF4jeDVl8g=",
          "dev": true
        },
        "semver": {
          "version": "6.3.0",
          "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.0.tgz",
          "integrity": "sha512-b39TBaTSfV6yBrapU89p5fKekE2m/NwnDocOVruQFS1/veMgdzuPcnOM34M6CwxW8jH/lxEa5rBoDeUwu5HHTw==",
          "dev": true
        }
      }
    },
    "stylus-loader": {
      "version": "6.2.0",
      "resolved": "https://registry.npmjs.org/stylus-loader/-/stylus-loader-6.2.0.tgz",
      "integrity": "sha512-5dsDc7qVQGRoc6pvCL20eYgRUxepZ9FpeK28XhdXaIPP6kXr6nI1zAAKFQgP5OBkOfKaURp4WUpJzspg1f01Gg==",
      "dev": true,
      "requires": {
        "fast-glob": "^3.2.7",
        "klona": "^2.0.4",
        "normalize-path": "^3.0.0"
      }
    },
    "supports-color": {
      "version": "5.5.0",
      "resolved": "https://registry.npmjs.org/supports-color/-/supports-color-5.5.0.tgz",
      "integrity": "sha512-QjVjwdXIt408MIiAqCX4oUKsgU2EqAGzs2Ppkm4aQYbjm+ZEWEcW4SfFNTr4uMNZma0ey4f5lgLrkB0aX0QMow==",
      "dev": true,
      "requires": {
        "has-flag": "^3.0.0"
      }
    },
    "symbol-observable": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/symbol-observable/-/symbol-observable-4.0.0.tgz",
      "integrity": "sha512-b19dMThMV4HVFynSAM1++gBHAbk2Tc/osgLIBZMKsyqh34jb2e8Os7T6ZW/Bt3pJFdBTd2JwAnAAEQV7rSNvcQ==",
      "dev": true
    },
    "tapable": {
      "version": "2.2.1",
      "resolved": "https://registry.npmjs.org/tapable/-/tapable-2.2.1.tgz",
      "integrity": "sha512-GNzQvQTOIP6RyTfE2Qxb8ZVlNmw0n88vp1szwWRimP02mnTsx3Wtn5qRdqY9w2XduFNUgvOwhNnQsjwCp+kqaQ==",
      "dev": true
    },
    "tar": {
      "version": "6.1.11",
      "resolved": "https://registry.npmjs.org/tar/-/tar-6.1.11.tgz",
      "integrity": "sha512-an/KZQzQUkZCkuoAA64hM92X0Urb6VpRhAFllDzz44U2mcD5scmT3zBc4VgVpkugF580+DQn8eAFSyoQt0tznA==",
      "dev": true,
      "requires": {
        "chownr": "^2.0.0",
        "fs-minipass": "^2.0.0",
        "minipass": "^3.0.0",
        "minizlib": "^2.1.1",
        "mkdirp": "^1.0.3",
        "yallist": "^4.0.0"
      }
    },
    "terser": {
      "version": "5.10.0",
      "resolved": "https://registry.npmjs.org/terser/-/terser-5.10.0.tgz",
      "integrity": "sha512-AMmF99DMfEDiRJfxfY5jj5wNH/bYO09cniSqhfoyxc8sFoYIgkJy86G04UoZU5VjlpnplVu0K6Tx6E9b5+DlHA==",
      "dev": true,
      "requires": {
        "commander": "^2.20.0",
        "source-map": "~0.7.2",
        "source-map-support": "~0.5.20"
      }
    },
    "terser-webpack-plugin": {
      "version": "5.3.0",
      "resolved": "https://registry.npmjs.org/terser-webpack-plugin/-/terser-webpack-plugin-5.3.0.tgz",
      "integrity": "sha512-LPIisi3Ol4chwAaPP8toUJ3L4qCM1G0wao7L3qNv57Drezxj6+VEyySpPw4B1HSO2Eg/hDY/MNF5XihCAoqnsQ==",
      "dev": true,
      "requires": {
        "jest-worker": "^27.4.1",
        "schema-utils": "^3.1.1",
        "serialize-javascript": "^6.0.0",
        "source-map": "^0.6.1",
        "terser": "^5.7.2"
      },
      "dependencies": {
        "ajv": {
          "version": "6.12.6",
          "resolved": "https://registry.npmjs.org/ajv/-/ajv-6.12.6.tgz",
          "integrity": "sha512-j3fVLgvTo527anyYyJOGTYJbG+vnnQYvE0m5mmkc1TK+nxAppkCLMIL0aZ4dblVCNoGShhm+kzE4ZUykBoMg4g==",
          "dev": true,
          "requires": {
            "fast-deep-equal": "^3.1.1",
            "fast-json-stable-stringify": "^2.0.0",
            "json-schema-traverse": "^0.4.1",
            "uri-js": "^4.2.2"
          }
        },
        "ajv-keywords": {
          "version": "3.5.2",
          "resolved": "https://registry.npmjs.org/ajv-keywords/-/ajv-keywords-3.5.2.tgz",
          "integrity": "sha512-5p6WTN0DdTGVQk6VjcEju19IgaHudalcfabD7yhDGeA6bcQnmL+CpveLJq/3hvfwd1aof6L386Ougkx6RfyMIQ==",
          "dev": true,
          "requires": {}
        },
        "json-schema-traverse": {
          "version": "0.4.1",
          "resolved": "https://registry.npmjs.org/json-schema-traverse/-/json-schema-traverse-0.4.1.tgz",
          "integrity": "sha512-xbbCH5dCYU5T8LcEhhuh7HJ88HXuW3qsI3Y0zOZFKfZEHcpWiHU/Jxzk629Brsab/mMiHQti9wMP+845RPe3Vg==",
          "dev": true
        },
        "schema-utils": {
          "version": "3.1.1",
          "resolved": "https://registry.npmjs.org/schema-utils/-/schema-utils-3.1.1.tgz",
          "integrity": "sha512-Y5PQxS4ITlC+EahLuXaY86TXfR7Dc5lw294alXOq86JAHCihAIZfqv8nNCWvaEJvaC51uN9hbLGeV0cFBdH+Fw==",
          "dev": true,
          "requires": {
            "@types/json-schema": "^7.0.8",
            "ajv": "^6.12.5",
            "ajv-keywords": "^3.5.2"
          }
        },
        "source-map": {
          "version": "0.6.1",
          "resolved": "https://registry.npmjs.org/source-map/-/source-map-0.6.1.tgz",
          "integrity": "sha512-UjgapumWlbMhkBgzT7Ykc5YXUT46F0iKu8SGXq0bcwP5dz/h0Plj6enJqjz1Zbq2l5WaqYnrVbwWOWMyF3F47g==",
          "dev": true
        }
      }
    },
    "test-exclude": {
      "version": "6.0.0",
      "resolved": "https://registry.npmjs.org/test-exclude/-/test-exclude-6.0.0.tgz",
      "integrity": "sha512-cAGWPIyOHU6zlmg88jwm7VRyXnMN7iV68OGAbYDk/Mh/xC/pzVPlQtY6ngoIH/5/tciuhGfvESU8GrHrcxD56w==",
      "dev": true,
      "requires": {
        "@istanbuljs/schema": "^0.1.2",
        "glob": "^7.1.4",
        "minimatch": "^3.0.4"
      }
    },
    "text-table": {
      "version": "0.2.0",
      "resolved": "https://registry.npmjs.org/text-table/-/text-table-0.2.0.tgz",
      "integrity": "sha1-f17oI66AUgfACvLfSoTsP8+lcLQ=",
      "dev": true
    },
    "through": {
      "version": "2.3.8",
      "resolved": "https://registry.npmjs.org/through/-/through-2.3.8.tgz",
      "integrity": "sha1-DdTJ/6q8NXlgsbckEV1+Doai4fU=",
      "dev": true
    },
    "thunky": {
      "version": "1.1.0",
      "resolved": "https://registry.npmjs.org/thunky/-/thunky-1.1.0.tgz",
      "integrity": "sha512-eHY7nBftgThBqOyHGVN+l8gF0BucP09fMo0oO/Lb0w1OF80dJv+lDVpXG60WMQvkcxAkNybKsrEIE3ZtKGmPrA==",
      "dev": true
    },
    "tmp": {
      "version": "0.0.33",
      "resolved": "https://registry.npmjs.org/tmp/-/tmp-0.0.33.tgz",
      "integrity": "sha512-jRCJlojKnZ3addtTOjdIqoRuPEKBvNXcGYqzO6zWZX8KfKEpnGY5jfggJQ3EjKuu8D4bJRr0y+cYJFmYbImXGw==",
      "dev": true,
      "requires": {
        "os-tmpdir": "~1.0.2"
      }
    },
    "to-fast-properties": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/to-fast-properties/-/to-fast-properties-2.0.0.tgz",
      "integrity": "sha1-3F5pjL0HkmW8c+A3doGk5Og/YW4=",
      "dev": true
    },
    "to-readable-stream": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/to-readable-stream/-/to-readable-stream-1.0.0.tgz",
      "integrity": "sha512-Iq25XBt6zD5npPhlLVXGFN3/gyR2/qODcKNNyTMd4vbm39HUaOiAM4PMq0eMVC/Tkxz+Zjdsc55g9yyz+Yq00Q=="
    },
    "to-regex-range": {
      "version": "5.0.1",
      "resolved": "https://registry.npmjs.org/to-regex-range/-/to-regex-range-5.0.1.tgz",
      "integrity": "sha512-65P7iz6X5yEr1cwcgvQxbbIw7Uk3gOy5dIdtZ4rDveLqhrdJP+Li/Hx6tyK0NEb+2GCyneCMJiGqrADCSNk8sQ==",
      "dev": true,
      "requires": {
        "is-number": "^7.0.0"
      }
    },
    "toidentifier": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/toidentifier/-/toidentifier-1.0.1.tgz",
      "integrity": "sha512-o5sSPKEkg/DIQNmH43V0/uerLrpzVedkUh8tGNvaeXpfpuwjKenlSox/2O/BTlZUtEe+JG7s5YhEz608PlAHRA=="
    },
    "tree-kill": {
      "version": "1.2.2",
      "resolved": "https://registry.npmjs.org/tree-kill/-/tree-kill-1.2.2.tgz",
      "integrity": "sha512-L0Orpi8qGpRG//Nd+H90vFB+3iHnue1zSSGmNOOCh1GLJ7rUKVwV2HvijphGQS2UmhUZewS9VgvxYIdgr+fG1A==",
      "dev": true
    },
    "tslib": {
      "version": "2.3.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.3.1.tgz",
      "integrity": "sha512-77EbyPPpMz+FRFRuAFlWMtmgUWGe9UOG2Z25NqCwiIjRhOf5iKGuzSe5P2w1laq+FkRy4p+PCuVkJSGkzTEKVw=="
    },
    "type-fest": {
      "version": "0.21.3",
      "resolved": "https://registry.npmjs.org/type-fest/-/type-fest-0.21.3.tgz",
      "integrity": "sha512-t0rzBq87m3fVcduHDUFhKmyyX+9eo6WQjZvf51Ea/M0Q7+T374Jp1aUiyUl0GKxp8M/OETVHSDvmkyPgvX+X2w==",
      "dev": true
    },
    "type-is": {
      "version": "1.6.18",
      "resolved": "https://registry.npmjs.org/type-is/-/type-is-1.6.18.tgz",
      "integrity": "sha512-TkRKr9sUTxEH8MdfuCSP7VizJyzRNMjj2J2do2Jr3Kym598JVdEksuzPQCnlFPW4ky9Q+iA+ma9BGm06XQBy8g==",
      "requires": {
        "media-typer": "0.3.0",
        "mime-types": "~2.1.24"
      }
    },
    "typed-assert": {
      "version": "1.0.8",
      "resolved": "https://registry.npmjs.org/typed-assert/-/typed-assert-1.0.8.tgz",
      "integrity": "sha512-5NkbXZUlmCE73Fs7gvkp1XXJWHYetPkg60QnQ2NXQmBYNFxbBr2zA8GCtaH4K2s2WhOmSlgiSTmrjrcm5tnM5g==",
      "dev": true
    },
    "typedarray-to-buffer": {
      "version": "3.1.5",
      "resolved": "https://registry.npmjs.org/typedarray-to-buffer/-/typedarray-to-buffer-3.1.5.tgz",
      "integrity": "sha512-zdu8XMNEDepKKR+XYOXAVPtWui0ly0NtohUscw+UmaHiAWT8hrV1rr//H6V+0DvJ3OQ19S979M0laLfX8rm82Q==",
      "requires": {
        "is-typedarray": "^1.0.0"
      }
    },
    "typescript": {
      "version": "4.5.5",
      "resolved": "https://registry.npmjs.org/typescript/-/typescript-4.5.5.tgz",
      "integrity": "sha512-TCTIul70LyWe6IJWT8QSYeA54WQe8EjQFU4wY52Fasj5UKx88LNYKCgBEHcOMOrFF1rKGbD8v/xcNWVUq9SymA==",
      "dev": true
    },
    "ua-parser-js": {
      "version": "0.7.31",
      "resolved": "https://registry.npmjs.org/ua-parser-js/-/ua-parser-js-0.7.31.tgz",
      "integrity": "sha512-qLK/Xe9E2uzmYI3qLeOmI0tEOt+TBBQyUIAh4aAgU05FVYzeZrKUdkAZfBNVGRaHVgV0TDkdEngJSw/SyQchkQ==",
      "dev": true
    },
    "unicode-canonical-property-names-ecmascript": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/unicode-canonical-property-names-ecmascript/-/unicode-canonical-property-names-ecmascript-2.0.0.tgz",
      "integrity": "sha512-yY5PpDlfVIU5+y/BSCxAJRBIS1Zc2dDG3Ujq+sR0U+JjUevW2JhocOF+soROYDSaAezOzOKuyyixhD6mBknSmQ==",
      "dev": true
    },
    "unicode-match-property-ecmascript": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/unicode-match-property-ecmascript/-/unicode-match-property-ecmascript-2.0.0.tgz",
      "integrity": "sha512-5kaZCrbp5mmbz5ulBkDkbY0SsPOjKqVS35VpL9ulMPfSl0J0Xsm+9Evphv9CoIZFwre7aJoa94AY6seMKGVN5Q==",
      "dev": true,
      "requires": {
        "unicode-canonical-property-names-ecmascript": "^2.0.0",
        "unicode-property-aliases-ecmascript": "^2.0.0"
      }
    },
    "unicode-match-property-value-ecmascript": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/unicode-match-property-value-ecmascript/-/unicode-match-property-value-ecmascript-2.0.0.tgz",
      "integrity": "sha512-7Yhkc0Ye+t4PNYzOGKedDhXbYIBe1XEQYQxOPyhcXNMJ0WCABqqj6ckydd6pWRZTHV4GuCPKdBAUiMc60tsKVw==",
      "dev": true
    },
    "unicode-property-aliases-ecmascript": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/unicode-property-aliases-ecmascript/-/unicode-property-aliases-ecmascript-2.0.0.tgz",
      "integrity": "sha512-5Zfuy9q/DFr4tfO7ZPeVXb1aPoeQSdeFMLpYuFebehDAhbuevLs5yxSZmIFN1tP5F9Wl4IpJrYojg85/zgyZHQ==",
      "dev": true
    },
    "unique-filename": {
      "version": "1.1.1",
      "resolved": "https://registry.npmjs.org/unique-filename/-/unique-filename-1.1.1.tgz",
      "integrity": "sha512-Vmp0jIp2ln35UTXuryvjzkjGdRyf9b2lTXuSYUiPmzRcl3FDtYqAwOnTJkAngD9SWhnoJzDbTKwaOrZ+STtxNQ==",
      "dev": true,
      "requires": {
        "unique-slug": "^2.0.0"
      }
    },
    "unique-slug": {
      "version": "2.0.2",
      "resolved": "https://registry.npmjs.org/unique-slug/-/unique-slug-2.0.2.tgz",
      "integrity": "sha512-zoWr9ObaxALD3DOPfjPSqxt4fnZiWblxHIgeWqW8x7UqDzEtHEQLzji2cuJYQFCU6KmoJikOYAZlrTHHebjx2w==",
      "dev": true,
      "requires": {
        "imurmurhash": "^0.1.4"
      }
    },
    "unique-string": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/unique-string/-/unique-string-2.0.0.tgz",
      "integrity": "sha512-uNaeirEPvpZWSgzwsPGtU2zVSTrn/8L5q/IexZmH0eH6SA73CmAA5U4GwORTxQAZs95TAXLNqeLoPPNO5gZfWg==",
      "requires": {
        "crypto-random-string": "^2.0.0"
      }
    },
    "universalify": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/universalify/-/universalify-2.0.0.tgz",
      "integrity": "sha512-hAZsKq7Yy11Zu1DE0OzWjw7nnLZmJZYTDZZyEFHZdUhV8FkH5MCfoU1XMaxXovpyW5nq5scPqq0ZDP9Zyl04oQ==",
      "dev": true
    },
    "unpipe": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/unpipe/-/unpipe-1.0.0.tgz",
      "integrity": "sha1-sr9O6FFKrmFltIF4KdIbLvSZBOw="
    },
    "update-notifier": {
      "version": "5.1.0",
      "resolved": "https://registry.npmjs.org/update-notifier/-/update-notifier-5.1.0.tgz",
      "integrity": "sha512-ItnICHbeMh9GqUy31hFPrD1kcuZ3rpxDZbf4KUDavXwS0bW5m7SLbDQpGX3UYr072cbrF5hFUs3r5tUsPwjfHw==",
      "requires": {
        "boxen": "^5.0.0",
        "chalk": "^4.1.0",
        "configstore": "^5.0.1",
        "has-yarn": "^2.1.0",
        "import-lazy": "^2.1.0",
        "is-ci": "^2.0.0",
        "is-installed-globally": "^0.4.0",
        "is-npm": "^5.0.0",
        "is-yarn-global": "^0.3.0",
        "latest-version": "^5.1.0",
        "pupa": "^2.1.1",
        "semver": "^7.3.4",
        "semver-diff": "^3.1.1",
        "xdg-basedir": "^4.0.0"
      },
      "dependencies": {
        "ansi-styles": {
          "version": "4.3.0",
          "resolved": "https://registry.npmjs.org/ansi-styles/-/ansi-styles-4.3.0.tgz",
          "integrity": "sha512-zbB9rCJAT1rbjiVDb2hqKFHNYLxgtk8NURxZ3IZwD3F6NtxbXZQCnnSi1Lkx+IDohdPlFp222wVALIheZJQSEg==",
          "requires": {
            "color-convert": "^2.0.1"
          }
        },
        "chalk": {
          "version": "4.1.2",
          "resolved": "https://registry.npmjs.org/chalk/-/chalk-4.1.2.tgz",
          "integrity": "sha512-oKnbhFyRIXpUuez8iBMmyEa4nbj4IOQyuhc/wy9kY7/WVPcwIO9VA668Pu8RkO7+0G76SLROeyw9CpQ061i4mA==",
          "requires": {
            "ansi-styles": "^4.1.0",
            "supports-color": "^7.1.0"
          }
        },
        "color-convert": {
          "version": "2.0.1",
          "resolved": "https://registry.npmjs.org/color-convert/-/color-convert-2.0.1.tgz",
          "integrity": "sha512-RRECPsj7iu/xb5oKYcsFHSppFNnsj/52OVTRKb4zP5onXwVF3zVmmToNcOfGC+CRDpfK/U584fMg38ZHCaElKQ==",
          "requires": {
            "color-name": "~1.1.4"
          }
        },
        "color-name": {
          "version": "1.1.4",
          "resolved": "https://registry.npmjs.org/color-name/-/color-name-1.1.4.tgz",
          "integrity": "sha512-dOy+3AuW3a2wNbZHIuMZpTcgjGuLU/uBL/ubcZF9OXbDo8ff4O8yVp5Bf0efS8uEoYo5q4Fx7dY9OgQGXgAsQA=="
        },
        "has-flag": {
          "version": "4.0.0",
          "resolved": "https://registry.npmjs.org/has-flag/-/has-flag-4.0.0.tgz",
          "integrity": "sha512-EykJT/Q1KjTWctppgIAgfSO0tKVuZUjhgMr17kqTumMl6Afv3EISleU7qZUzoXDFTAHTDC4NOoG/ZxU3EvlMPQ=="
        },
        "supports-color": {
          "version": "7.2.0",
          "resolved": "https://registry.npmjs.org/supports-color/-/supports-color-7.2.0.tgz",
          "integrity": "sha512-qpCAvRl9stuOHveKsn7HncJRvv501qIacKzQlO/+Lwxc9+0q2wLyv4Dfvt80/DPn2pqOBsJdDiogXGR9+OvwRw==",
          "requires": {
            "has-flag": "^4.0.0"
          }
        }
      }
    },
    "uri-js": {
      "version": "4.4.1",
      "resolved": "https://registry.npmjs.org/uri-js/-/uri-js-4.4.1.tgz",
      "integrity": "sha512-7rKUyy33Q1yc98pQ1DAmLtwX109F7TIfWlW1Ydo8Wl1ii1SeHieeh0HHfPeL2fMXK6z0s8ecKs9frCuLJvndBg==",
      "dev": true,
      "requires": {
        "punycode": "^2.1.0"
      }
    },
    "url": {
      "version": "0.11.0",
      "resolved": "https://registry.npmjs.org/url/-/url-0.11.0.tgz",
      "integrity": "sha1-ODjpfPxgUh63PFJajlW/3Z4uKPE=",
      "dev": true,
      "requires": {
        "punycode": "1.3.2",
        "querystring": "0.2.0"
      },
      "dependencies": {
        "punycode": {
          "version": "1.3.2",
          "resolved": "https://registry.npmjs.org/punycode/-/punycode-1.3.2.tgz",
          "integrity": "sha1-llOgNvt8HuQjQvIyXM7v6jkmxI0=",
          "dev": true
        }
      }
    },
    "url-parse-lax": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/url-parse-lax/-/url-parse-lax-3.0.0.tgz",
      "integrity": "sha1-FrXK/Afb42dsGxmZF3gj1lA6yww=",
      "requires": {
        "prepend-http": "^2.0.0"
      }
    },
    "util-deprecate": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/util-deprecate/-/util-deprecate-1.0.2.tgz",
      "integrity": "sha1-RQ1Nyfpw3nMnYvvS1KKJgUGaDM8=",
      "dev": true
    },
    "utils-merge": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/utils-merge/-/utils-merge-1.0.1.tgz",
      "integrity": "sha1-n5VxD1CiZ5R7LMwSR0HBAoQn5xM="
    },
    "uuid": {
      "version": "8.3.2",
      "resolved": "https://registry.npmjs.org/uuid/-/uuid-8.3.2.tgz",
      "integrity": "sha512-+NYs2QeMWy+GWFOEm9xnn6HCDp0l7QBD7ml8zLUmJ+93Q5NF0NocErnwkTkXVFNiX3/fpC6afS8Dhb/gz7R7eg==",
      "dev": true
    },
    "validate-npm-package-name": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/validate-npm-package-name/-/validate-npm-package-name-3.0.0.tgz",
      "integrity": "sha1-X6kS2B630MdK/BQN5zF/DKffQ34=",
      "dev": true,
      "requires": {
        "builtins": "^1.0.3"
      }
    },
    "vary": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/vary/-/vary-1.1.2.tgz",
      "integrity": "sha1-IpnwLG3tMNSllhsLn3RSShj2NPw="
    },
    "void-elements": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/void-elements/-/void-elements-2.0.1.tgz",
      "integrity": "sha1-wGavtYK7HLQSjWDqkjkulNXp2+w=",
      "dev": true
    },
    "watchpack": {
      "version": "2.3.1",
      "resolved": "https://registry.npmjs.org/watchpack/-/watchpack-2.3.1.tgz",
      "integrity": "sha512-x0t0JuydIo8qCNctdDrn1OzH/qDzk2+rdCOC3YzumZ42fiMqmQ7T3xQurykYMhYfHaPHTp4ZxAx2NfUo1K6QaA==",
      "dev": true,
      "requires": {
        "glob-to-regexp": "^0.4.1",
        "graceful-fs": "^4.1.2"
      }
    },
    "wbuf": {
      "version": "1.7.3",
      "resolved": "https://registry.npmjs.org/wbuf/-/wbuf-1.7.3.tgz",
      "integrity": "sha512-O84QOnr0icsbFGLS0O3bI5FswxzRr8/gHwWkDlQFskhSPryQXvrTMxjxGP4+iWYoauLoBvfDpkrOauZ+0iZpDA==",
      "dev": true,
      "requires": {
        "minimalistic-assert": "^1.0.0"
      }
    },
    "wcwidth": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/wcwidth/-/wcwidth-1.0.1.tgz",
      "integrity": "sha1-8LDc+RW8X/FSivrbLA4XtTLaL+g=",
      "dev": true,
      "requires": {
        "defaults": "^1.0.3"
      }
    },
    "webpack": {
      "version": "5.65.0",
      "resolved": "https://registry.npmjs.org/webpack/-/webpack-5.65.0.tgz",
      "integrity": "sha512-Q5or2o6EKs7+oKmJo7LaqZaMOlDWQse9Tm5l1WAfU/ujLGN5Pb0SqGeVkN/4bpPmEqEP5RnVhiqsOtWtUVwGRw==",
      "dev": true,
      "requires": {
        "@types/eslint-scope": "^3.7.0",
        "@types/estree": "^0.0.50",
        "@webassemblyjs/ast": "1.11.1",
        "@webassemblyjs/wasm-edit": "1.11.1",
        "@webassemblyjs/wasm-parser": "1.11.1",
        "acorn": "^8.4.1",
        "acorn-import-assertions": "^1.7.6",
        "browserslist": "^4.14.5",
        "chrome-trace-event": "^1.0.2",
        "enhanced-resolve": "^5.8.3",
        "es-module-lexer": "^0.9.0",
        "eslint-scope": "5.1.1",
        "events": "^3.2.0",
        "glob-to-regexp": "^0.4.1",
        "graceful-fs": "^4.2.4",
        "json-parse-better-errors": "^1.0.2",
        "loader-runner": "^4.2.0",
        "mime-types": "^2.1.27",
        "neo-async": "^2.6.2",
        "schema-utils": "^3.1.0",
        "tapable": "^2.1.1",
        "terser-webpack-plugin": "^5.1.3",
        "watchpack": "^2.3.1",
        "webpack-sources": "^3.2.2"
      },
      "dependencies": {
        "ajv": {
          "version": "6.12.6",
          "resolved": "https://registry.npmjs.org/ajv/-/ajv-6.12.6.tgz",
          "integrity": "sha512-j3fVLgvTo527anyYyJOGTYJbG+vnnQYvE0m5mmkc1TK+nxAppkCLMIL0aZ4dblVCNoGShhm+kzE4ZUykBoMg4g==",
          "dev": true,
          "requires": {
            "fast-deep-equal": "^3.1.1",
            "fast-json-stable-stringify": "^2.0.0",
            "json-schema-traverse": "^0.4.1",
            "uri-js": "^4.2.2"
          }
        },
        "ajv-keywords": {
          "version": "3.5.2",
          "resolved": "https://registry.npmjs.org/ajv-keywords/-/ajv-keywords-3.5.2.tgz",
          "integrity": "sha512-5p6WTN0DdTGVQk6VjcEju19IgaHudalcfabD7yhDGeA6bcQnmL+CpveLJq/3hvfwd1aof6L386Ougkx6RfyMIQ==",
          "dev": true,
          "requires": {}
        },
        "json-schema-traverse": {
          "version": "0.4.1",
          "resolved": "https://registry.npmjs.org/json-schema-traverse/-/json-schema-traverse-0.4.1.tgz",
          "integrity": "sha512-xbbCH5dCYU5T8LcEhhuh7HJ88HXuW3qsI3Y0zOZFKfZEHcpWiHU/Jxzk629Brsab/mMiHQti9wMP+845RPe3Vg==",
          "dev": true
        },
        "schema-utils": {
          "version": "3.1.1",
          "resolved": "https://registry.npmjs.org/schema-utils/-/schema-utils-3.1.1.tgz",
          "integrity": "sha512-Y5PQxS4ITlC+EahLuXaY86TXfR7Dc5lw294alXOq86JAHCihAIZfqv8nNCWvaEJvaC51uN9hbLGeV0cFBdH+Fw==",
          "dev": true,
          "requires": {
            "@types/json-schema": "^7.0.8",
            "ajv": "^6.12.5",
            "ajv-keywords": "^3.5.2"
          }
        }
      }
    },
    "webpack-dev-middleware": {
      "version": "5.2.2",
      "resolved": "https://registry.npmjs.org/webpack-dev-middleware/-/webpack-dev-middleware-5.2.2.tgz",
      "integrity": "sha512-DjZyYrsHhkikAFNvSNKrpnziXukU1EChFAh9j4LAm6ndPLPW8cN0KhM7T+RAiOqsQ6ABfQ8hoKIs9IWMTjov+w==",
      "dev": true,
      "requires": {
        "colorette": "^2.0.10",
        "memfs": "^3.2.2",
        "mime-types": "^2.1.31",
        "range-parser": "^1.2.1",
        "schema-utils": "^4.0.0"
      },
      "dependencies": {
        "schema-utils": {
          "version": "4.0.0",
          "resolved": "https://registry.npmjs.org/schema-utils/-/schema-utils-4.0.0.tgz",
          "integrity": "sha512-1edyXKgh6XnJsJSQ8mKWXnN/BVaIbFMLpouRUrXgVq7WYne5kw3MW7UPhO44uRXQSIpTSXoJbmrR2X0w9kUTyg==",
          "dev": true,
          "requires": {
            "@types/json-schema": "^7.0.9",
            "ajv": "^8.8.0",
            "ajv-formats": "^2.1.1",
            "ajv-keywords": "^5.0.0"
          }
        }
      }
    },
    "webpack-dev-server": {
      "version": "4.6.0",
      "resolved": "https://registry.npmjs.org/webpack-dev-server/-/webpack-dev-server-4.6.0.tgz",
      "integrity": "sha512-oojcBIKvx3Ya7qs1/AVWHDgmP1Xml8rGsEBnSobxU/UJSX1xP1GPM3MwsAnDzvqcVmVki8tV7lbcsjEjk0PtYg==",
      "dev": true,
      "requires": {
        "ansi-html-community": "^0.0.8",
        "bonjour": "^3.5.0",
        "chokidar": "^3.5.2",
        "colorette": "^2.0.10",
        "compression": "^1.7.4",
        "connect-history-api-fallback": "^1.6.0",
        "default-gateway": "^6.0.3",
        "del": "^6.0.0",
        "express": "^4.17.1",
        "graceful-fs": "^4.2.6",
        "html-entities": "^2.3.2",
        "http-proxy-middleware": "^2.0.0",
        "ipaddr.js": "^2.0.1",
        "open": "^8.0.9",
        "p-retry": "^4.5.0",
        "portfinder": "^1.0.28",
        "schema-utils": "^4.0.0",
        "selfsigned": "^1.10.11",
        "serve-index": "^1.9.1",
        "sockjs": "^0.3.21",
        "spdy": "^4.0.2",
        "strip-ansi": "^7.0.0",
        "url": "^0.11.0",
        "webpack-dev-middleware": "^5.2.1",
        "ws": "^8.1.0"
      },
      "dependencies": {
        "ansi-regex": {
          "version": "6.0.1",
          "resolved": "https://registry.npmjs.org/ansi-regex/-/ansi-regex-6.0.1.tgz",
          "integrity": "sha512-n5M855fKb2SsfMIiFFoVrABHJC8QtHwVx+mHWP3QcEqBHYienj5dHSgjbxtC0WEZXYt4wcD6zrQElDPhFuZgfA==",
          "dev": true
        },
        "schema-utils": {
          "version": "4.0.0",
          "resolved": "https://registry.npmjs.org/schema-utils/-/schema-utils-4.0.0.tgz",
          "integrity": "sha512-1edyXKgh6XnJsJSQ8mKWXnN/BVaIbFMLpouRUrXgVq7WYne5kw3MW7UPhO44uRXQSIpTSXoJbmrR2X0w9kUTyg==",
          "dev": true,
          "requires": {
            "@types/json-schema": "^7.0.9",
            "ajv": "^8.8.0",
            "ajv-formats": "^2.1.1",
            "ajv-keywords": "^5.0.0"
          }
        },
        "strip-ansi": {
          "version": "7.0.1",
          "resolved": "https://registry.npmjs.org/strip-ansi/-/strip-ansi-7.0.1.tgz",
          "integrity": "sha512-cXNxvT8dFNRVfhVME3JAe98mkXDYN2O1l7jmcwMnOslDeESg1rF/OZMtK0nRAhiari1unG5cD4jG3rapUAkLbw==",
          "dev": true,
          "requires": {
            "ansi-regex": "^6.0.1"
          }
        }
      }
    },
    "webpack-merge": {
      "version": "5.8.0",
      "resolved": "https://registry.npmjs.org/webpack-merge/-/webpack-merge-5.8.0.tgz",
      "integrity": "sha512-/SaI7xY0831XwP6kzuwhKWVKDP9t1QY1h65lAFLbZqMPIuYcD9QAW4u9STIbU9kaJbPBB/geU/gLr1wDjOhQ+Q==",
      "dev": true,
      "requires": {
        "clone-deep": "^4.0.1",
        "wildcard": "^2.0.0"
      }
    },
    "webpack-sources": {
      "version": "3.2.3",
      "resolved": "https://registry.npmjs.org/webpack-sources/-/webpack-sources-3.2.3.tgz",
      "integrity": "sha512-/DyMEOrDgLKKIG0fmvtz+4dUX/3Ghozwgm6iPp8KRhvn+eQf9+Q7GWxVNMk3+uCPWfdXYC4ExGBckIXdFEfH1w==",
      "dev": true
    },
    "webpack-subresource-integrity": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/webpack-subresource-integrity/-/webpack-subresource-integrity-5.0.0.tgz",
      "integrity": "sha512-x9514FpLRydO+UAQ8DY4aLtCjxmdLkuQVcDFN1kGzuusREYJ1B0rzk/iIlWiL6dnvrhEGFj2+UsdxDkP8Z4UKg==",
      "dev": true,
      "requires": {
        "typed-assert": "^1.0.8"
      }
    },
    "websocket-driver": {
      "version": "0.7.4",
      "resolved": "https://registry.npmjs.org/websocket-driver/-/websocket-driver-0.7.4.tgz",
      "integrity": "sha512-b17KeDIQVjvb0ssuSDF2cYXSg2iztliJ4B9WdsuB6J952qCPKmnVq4DyW5motImXHDC1cBT/1UezrJVsKw5zjg==",
      "dev": true,
      "requires": {
        "http-parser-js": ">=0.5.1",
        "safe-buffer": ">=5.1.0",
        "websocket-extensions": ">=0.1.1"
      }
    },
    "websocket-extensions": {
      "version": "0.1.4",
      "resolved": "https://registry.npmjs.org/websocket-extensions/-/websocket-extensions-0.1.4.tgz",
      "integrity": "sha512-OqedPIGOfsDlo31UNwYbCFMSaO9m9G/0faIHj5/dZFDMFqPTcx6UwqyOy3COEaEOg/9VsGIpdqn62W5KhoKSpg==",
      "dev": true
    },
    "which": {
      "version": "1.3.1",
      "resolved": "https://registry.npmjs.org/which/-/which-1.3.1.tgz",
      "integrity": "sha512-HxJdYWq1MTIQbJ3nw0cqssHoTNU267KlrDuGZ1WYlxDStUtKUhOaJmh112/TZmHxxUfuJqPXSOm7tDyas0OSIQ==",
      "dev": true,
      "requires": {
        "isexe": "^2.0.0"
      }
    },
    "wide-align": {
      "version": "1.1.5",
      "resolved": "https://registry.npmjs.org/wide-align/-/wide-align-1.1.5.tgz",
      "integrity": "sha512-eDMORYaPNZ4sQIuuYPDHdQvf4gyCF9rEEV/yPxGfwPkRodwEgiMUUXTx/dex+Me0wxx53S+NgUHaP7y3MGlDmg==",
      "dev": true,
      "requires": {
        "string-width": "^1.0.2 || 2 || 3 || 4"
      }
    },
    "widest-line": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/widest-line/-/widest-line-3.1.0.tgz",
      "integrity": "sha512-NsmoXalsWVDMGupxZ5R08ka9flZjjiLvHVAWYOKtiKM8ujtZWr9cRffak+uSE48+Ob8ObalXpwyeUiyDD6QFgg==",
      "requires": {
        "string-width": "^4.0.0"
      }
    },
    "wildcard": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/wildcard/-/wildcard-2.0.0.tgz",
      "integrity": "sha512-JcKqAHLPxcdb9KM49dufGXn2x3ssnfjbcaQdLlfZsL9rH9wgDQjUtDxbo8NE0F6SFvydeu1VhZe7hZuHsB2/pw==",
      "dev": true
    },
    "wrap-ansi": {
      "version": "7.0.0",
      "resolved": "https://registry.npmjs.org/wrap-ansi/-/wrap-ansi-7.0.0.tgz",
      "integrity": "sha512-YVGIj2kamLSTxw6NsZjoBxfSwsn0ycdesmc4p+Q21c5zPuZ1pl+NfxVdxPtdHvmNVOQ6XSYG4AUtyt/Fi7D16Q==",
      "requires": {
        "ansi-styles": "^4.0.0",
        "string-width": "^4.1.0",
        "strip-ansi": "^6.0.0"
      },
      "dependencies": {
        "ansi-styles": {
          "version": "4.3.0",
          "resolved": "https://registry.npmjs.org/ansi-styles/-/ansi-styles-4.3.0.tgz",
          "integrity": "sha512-zbB9rCJAT1rbjiVDb2hqKFHNYLxgtk8NURxZ3IZwD3F6NtxbXZQCnnSi1Lkx+IDohdPlFp222wVALIheZJQSEg==",
          "requires": {
            "color-convert": "^2.0.1"
          }
        },
        "color-convert": {
          "version": "2.0.1",
          "resolved": "https://registry.npmjs.org/color-convert/-/color-convert-2.0.1.tgz",
          "integrity": "sha512-RRECPsj7iu/xb5oKYcsFHSppFNnsj/52OVTRKb4zP5onXwVF3zVmmToNcOfGC+CRDpfK/U584fMg38ZHCaElKQ==",
          "requires": {
            "color-name": "~1.1.4"
          }
        },
        "color-name": {
          "version": "1.1.4",
          "resolved": "https://registry.npmjs.org/color-name/-/color-name-1.1.4.tgz",
          "integrity": "sha512-dOy+3AuW3a2wNbZHIuMZpTcgjGuLU/uBL/ubcZF9OXbDo8ff4O8yVp5Bf0efS8uEoYo5q4Fx7dY9OgQGXgAsQA=="
        }
      }
    },
    "wrappy": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/wrappy/-/wrappy-1.0.2.tgz",
      "integrity": "sha1-tSQ9jz7BqjXxNkYFvA0QNuMKtp8="
    },
    "write-file-atomic": {
      "version": "3.0.3",
      "resolved": "https://registry.npmjs.org/write-file-atomic/-/write-file-atomic-3.0.3.tgz",
      "integrity": "sha512-AvHcyZ5JnSfq3ioSyjrBkH9yW4m7Ayk8/9My/DD9onKeu/94fwrMocemO2QAJFAlnnDN+ZDS+ZjAR5ua1/PV/Q==",
      "requires": {
        "imurmurhash": "^0.1.4",
        "is-typedarray": "^1.0.0",
        "signal-exit": "^3.0.2",
        "typedarray-to-buffer": "^3.1.5"
      }
    },
    "ws": {
      "version": "8.2.3",
      "resolved": "https://registry.npmjs.org/ws/-/ws-8.2.3.tgz",
      "integrity": "sha512-wBuoj1BDpC6ZQ1B7DWQBYVLphPWkm8i9Y0/3YdHjHKHiohOJ1ws+3OccDWtH+PoC9DZD5WOTrJvNbWvjS6JWaA==",
      "dev": true,
      "requires": {}
    },
    "xdg-basedir": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/xdg-basedir/-/xdg-basedir-4.0.0.tgz",
      "integrity": "sha512-PSNhEJDejZYV7h50BohL09Er9VaIefr2LMAf3OEmpCkjOi34eYyQYAXUTjEQtZJTKcF0E2UKTh+osDLsgNim9Q=="
    },
    "y18n": {
      "version": "5.0.8",
      "resolved": "https://registry.npmjs.org/y18n/-/y18n-5.0.8.tgz",
      "integrity": "sha512-0pfFzegeDWJHJIAmTLRP2DwHjdF5s7jo9tuztdQxAhINCdvS+3nGINqPd00AphqJR/0LhANUS6/+7SCb98YOfA=="
    },
    "yallist": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/yallist/-/yallist-4.0.0.tgz",
      "integrity": "sha512-3wdGidZyq5PB084XLES5TpOSRA3wjXAlIWMhum2kRcv/41Sn2emQ0dycQW4uZXLejwKvg6EsvbdlVL+FYEct7A=="
    },
    "yaml": {
      "version": "1.10.2",
      "resolved": "https://registry.npmjs.org/yaml/-/yaml-1.10.2.tgz",
      "integrity": "sha512-r3vXyErRCYJ7wg28yvBY5VSoAF8ZvlcW9/BwUzEtUsjvX/DKs24dIkuwjtuprwJJHsbyUbLApepYTR1BN4uHrg==",
      "dev": true
    },
    "yargs": {
      "version": "17.3.1",
      "resolved": "https://registry.npmjs.org/yargs/-/yargs-17.3.1.tgz",
      "integrity": "sha512-WUANQeVgjLbNsEmGk20f+nlHgOqzRFpiGWVaBrYGYIGANIIu3lWjoyi0fNlFmJkvfhCZ6BXINe7/W2O2bV4iaA==",
      "requires": {
        "cliui": "^7.0.2",
        "escalade": "^3.1.1",
        "get-caller-file": "^2.0.5",
        "require-directory": "^2.1.1",
        "string-width": "^4.2.3",
        "y18n": "^5.0.5",
        "yargs-parser": "^21.0.0"
      }
    },
    "yargs-parser": {
      "version": "21.0.0",
      "resolved": "https://registry.npmjs.org/yargs-parser/-/yargs-parser-21.0.0.tgz",
      "integrity": "sha512-z9kApYUOCwoeZ78rfRYYWdiU/iNL6mwwYlkkZfJoyMR1xps+NEBX5X7XmRpxkZHhXJ6+Ey00IwKxBBSW9FIjyA=="
    },
    "zone.js": {
      "version": "0.11.4",
      "resolved": "https://registry.npmjs.org/zone.js/-/zone.js-0.11.4.tgz",
      "integrity": "sha512-DDh2Ab+A/B+9mJyajPjHFPWfYU1H+pdun4wnnk0OcQTNjem1XQSZ2CDW+rfZEUDjv5M19SBqAkjZi0x5wuB5Qw==",
      "requires": {
        "tslib": "^2.0.0"
      }
    }
  }
}

# App

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 13.1.2.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.

/* To learn more about this file see: https://angular.io/config/tsconfig. */
{
  "extends": "./tsconfig.json",
  "compilerOptions": {
    "outDir": "./out-tsc/app",
    "types": []
  },
  "files": [
    "src/main.ts",
    "src/polyfills.ts"
  ],
  "include": [
    "src/**/*.d.ts"
  ]
}

/* To learn more about this file see: https://angular.io/config/tsconfig. */
{
  "compileOnSave": false,
  "compilerOptions": {
    "baseUrl": "./",
    "outDir": "./dist/out-tsc",
    "forceConsistentCasingInFileNames": true,
    "strict": true,
    "noImplicitOverride": true,
    "noPropertyAccessFromIndexSignature": true,
    "noImplicitReturns": true,
    "noFallthroughCasesInSwitch": true,
    "sourceMap": true,
    "declaration": false,
    "downlevelIteration": true,
    "experimentalDecorators": true,
    "moduleResolution": "node",
    "importHelpers": true,
    "target": "es2017",
    "module": "es2020",
    "lib": [
      "es2020",
      "dom"
    ]
  },
  "angularCompilerOptions": {
    "enableI18nLegacyMessageIdFormat": false,
    "strictInjectionParameters": true,
    "strictInputAccessModifiers": true,
    "strictTemplates": true
  }
}

/* To learn more about this file see: https://angular.io/config/tsconfig. */
{
  "extends": "./tsconfig.json",
  "compilerOptions": {
    "outDir": "./out-tsc/spec",
    "types": [
      "jasmine"
    ]
  },
  "files": [
    "src/test.ts",
    "src/polyfills.ts"
  ],
  "include": [
    "src/**/*.spec.ts",
    "src/**/*.d.ts"
  ]
}

# This file is used by the build system to adjust CSS and JS output to support the specified browsers below.
# For additional information regarding the format and rule options, please see:
# https://github.com/browserslist/browserslist#queries

# For the full list of supported browsers by the Angular framework, please see:
# https://angular.io/guide/browser-support

# You can see what browsers were selected by your queries by running:
#   npx browserslist

last 1 Chrome version
last 1 Firefox version
last 2 Edge major versions
last 2 Safari major versions
last 2 iOS major versions
Firefox ESR
