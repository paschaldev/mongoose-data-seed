# Snapshot report for `src/e2e/init.e2e.js`

The actual snapshot is saved in `init.e2e.js.snap`.

Generated by [AVA](https://ava.li).

## md-seed init --help

> Snapshot 1

    `␊
    [4m[1mInitialize mongoose-data-seed[22m[24m␊
    ␊
      Install mongoose-data-seed into your project.                                 ␊
      Generate md-seed-config.js, md-seed-generator.js and create seeders folder    ␊
    ␊
    [4m[1mSynopsis[22m[24m␊
    ␊
      $ md-seed init [[1m--seedersFolder[22m=[4mfolder-name[24m] [[1m--seederTemplate[22m=[4mfile-path[24m] ␊
      $ md-seed init [1m--help[22m                                                     ␊
    ␊
    [4m[1mOptions[22m[24m␊
    ␊
      [1m-f[22m, [1m--seedersFolder[22m [4mstring[24m    Seeders folder name       ␊
      [1m-t[22m, [1m--seederTemplate[22m [4mstring[24m   Seeder template file path ␊
      [1m-h[22m, [1m--help[22m                    Show usage guide          ␊
    `

## md-seed init --seedersFolder=folder-name seederTemplate=file-path.ejs

> log results

    [
      [
        '[32mCREATED[39m file-path.ejs',
      ],
      [
        '[32mUPDATED[39m package.json',
      ],
      [
        '[32mCREATED[39m folder-name',
      ],
      [
        '[32mCREATED[39m md-seed-config.js',
      ],
    ]

> sandbox content

    [
      {
        content: `import { Seeder } from 'mongoose-data-seed';␊
        import { Model } from '../server/models';␊
        ␊
        const data = [{␊
        ␊
        }];␊
        ␊
        class <%= seederName %>Seeder extends Seeder {␊
        ␊
          async shouldRun() {␊
            return Model.countDocuments().exec().then(count => count === 0);␊
          }␊
        ␊
          async run() {␊
            return Model.create(data);␊
          }␊
        }␊
        ␊
        export default <%= seederName %>Seeder;␊
        `,
        name: 'file-path.ejs',
      },
      {
        content: [],
        name: 'folder-name',
      },
      {
        content: `import mongoose from 'mongoose';␊
        ␊
        const mongoURL = process.env.MONGO_URL || 'mongodb://localhost:27017/dbname';␊
        ␊
        /**␊
         * Seeders List␊
         * order is important␊
         * @type {Object}␊
         */␊
        export const seedersList = {␊
        ␊
        };␊
        /**␊
         * Connect to mongodb implementation␊
         * @return {Promise}␊
         */␊
        export const connect = async () =>␊
          await mongoose.connect(mongoURL, { useNewUrlParser: true });␊
        /**␊
         * Drop/Clear the database implementation␊
         * @return {Promise}␊
         */␊
        export const dropdb = async () => mongoose.connection.db.dropDatabase();␊
        `,
        name: 'md-seed-config.js',
      },
      {
        content: `{␊
          "name": "md-seed-example",␊
          "version": "1.0.0",␊
          "description": "Example of using mongoose-data-seed",␊
          "main": "index.js",␊
          "scripts": {␊
            "test": "echo \\"Error: no test specified\\" && exit 1"␊
          },␊
          "author": "Avi Sharvit <sharvita@gmail.com> (https://sharvit.github.io)",␊
          "license": "MIT",␊
          "mdSeed": {␊
            "seedersFolder": "folder-name\\u001b",␊
            "customSeederTemplate": "file-path.ejs"␊
          },␊
          "dependencies": {␊
            "crypto": "0.0.3",␊
            "faker": "^4.1.0",␊
            "mongoose": "^5.0.0",␊
            "uid2": "0.0.3"␊
          },␊
          "devDependencies": {␊
            "@babel/preset-env": "^7.0.0"␊
          }␊
        }␊
        `,
        name: 'package.json',
      },
    ]