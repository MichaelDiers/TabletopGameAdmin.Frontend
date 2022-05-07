# TabletopGameAdmin.Frontend

## AngularJs Setup

### Angular CLI

```
npm install -g @angular/cli
```

### Create project

```
ng new [PROJECT NAME]
```

### Start the project

```
npm run start
```

### Additional npm scripts

```
"ci": "npm install && npm run build && npm run test:prod",
"test:prod": "ng test --browsers=ChromeHeadless --watch=false --code-coverage"
```

## Google cloud App Engine

### Add app.yaml

```
runtime: python310
api_version: 1
threadsafe: true

handlers:
- url: /
  static_files: tga/index.html
  upload: tga/index.html

- url: /index.html
  static_files: tga/index.html
  upload: tga/index.html

- url: /(.*\.(ico|js|css))$
  static_files: tga/\1
  upload: tga/.*\.(ico|js|css)$
```

### Add new script to package.json

```
"appengine": "cp app.yaml dist/app.yaml",
```