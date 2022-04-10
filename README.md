# EpidemicManagement

## Install

Enter schoolVirus-front and schoolVirus-back, execute the command.

```
$ npm install
```
if error
```
$ npm install --legacy-peer-deps
```

## Usage

### Run the front directly

Enter schoolVirus-front:

```
$ npm run dev
```

### Run front and back together

Create a database and import the sql file.

Enter schoolVirus-back/config/config.json and modify database account password in the development configuration.

Enter schoolVirus-back folder:

```
$ node app.js
```

Enter schoolVirus-front folder:

```
$ npm run dev
```

## Password

Student Role account & password: 11111111 & 123456

Teacher Role account & password: 22222222 & 123456

Admin Role account & password: 33333333 & a123456
