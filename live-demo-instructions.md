#Live Demo

The Services are hosted at Digital Ocean at the given IP 104.131.51.202.

The DRF service is running on *uwsgi* and using *nginx* for proxing and serve django static files and using the default sqlite database.

Currently the Go service is running on the same machine at :3001 for the api services and :8080 for uploaded files serving. I COULD use nginx *location* rules to serve everything at :80 but since Go's native HttpServer is even faster than nginx I decided to leave it handling the connections directly (which is fun for experimenting and low visibility services, but unrecommended for real world production on highly visible services, although golang is much safer than C, execution-wise, nginx is a fairly proved software).

`curl -F "uploadfile=@/PATH/TO/YOU/IMAGE.JPG" 104.131.51.202:3001/chopit/onyotestuser`

    Accessing Puzzler DRF entrypoint:
        http://104.131.51.202

    Web Authentication:
        user: admin // pwd: teste123

    `http://104.131.51.202/puzzles/1/` -> 405

Getting a puzzle:
    `curl -X OPTIONS http://admin:teste123@104.131.51.202/puzzles/1`

Providing a solution to it:
    `curl -H "Content-Type: application/json" -X PUT -d '{"sequence": ["cf98d0c129fdd45ec6b7d4ab1fb73bdb", "a0d7576a2a8b514e08e08544a42bdaaa", "c63cbd1abb4ef70df7c6e8acf5d6a415", "7f1637714caf97728f430b7ee4577bb2", "f323ab3fc1737556a3914f5f8675a0a3", "c09dcdd9e8979a31cd072f1c6f3220b3", "aa1330d57d3a7a48a67f1157b93dcc10", "c52635ec37ae4d0702a6ff6121bdd00a", "0f8572dc29031274f3039396a4fa44f3", "fbd2dc72528299e7e9a107312a86ee75", "2f221a18eb86380369570b2ed147d8b4", "4f57d0ecf9622a0bd8a6e3f79c71a09d", "98c1d2a9d58ce748c08cf65dd3354676", "f951c0a95f3bb41ebd96e11f9e0fc86a", "a70c48e27d2297e32fe2a9012c3b7b44", "732e85325ff107fa2e63441c5db5104f", "2d2b7764882d2072866d003dac1f94db", "a4bbcd84c66d4117cd2eaac14b7cef81", "68915b6586b6ed73dea4c064e470e1f0", "6151f5ab282d90e4cee404433b271dda", "e61730e6717b1787cf09d44914ffb920", "453e406dcee4d18174d4ff623f52dcd8", "f69160b1cad6fbca61df4004d739ebea", "2cec0f1fa2a7fef6036e3c3476571065", "a6f2ab895b6e5c01915d054aa383da5a", "63a6e25ccc032f52387d07fa4433a95e", "f989fa70c7bf24332027eed5222ed4f8", "c54cef8a015c497bd986e4af98d48234", "b425e0c75591aa8fcea1aeb2e03b5944", "bc5861c5c13a0b0659a923b6b51a3878", "e0260672e1e9df5ae441cabeebcc1b5a", "d3205b316e68a2d08b83b5785cabb27a", "de76b774f7eff4ec70900dbdc8a6e2a8", "7e114f494071474eded2cf941ff8e8b5", "ada5dd8970b1b9d519d88604794b10ac", "59ccc3e2a620b7f7ef6840621379e7a7", "8d6638d51ae352e5afd4c11ad006dbe1", "a4e1cd317d54f0878d6baec98779ae2c", "6b735339cb51138bf18b8f3db482e777", "b7301e97c127a09b3ad128053f74307a", "11fe06b7914f335e2c6e05fc46ed1060", "afe1a52c4f7f5da8b3b7c53b1dc75cc3", "c1bd8f65edb4be1548cc3f6e7c7a9dd1", "d19c5eaf6bbebd72cecd36aff9727f51", "fd48d5bd74b03ae960369d6650062e8e", "abf3248a8d85d309aaea633da6373b53", "0f42756e5788f9b032b84d100355f1e6", "79cef6701281790dab3660e3be102291", "a8de7beface6298b915977a11490ddf4", "0dfb91a1509eb88cd90bad51cdeeedc1", "15d69c4a53a029f8e00797ed989167c4", "2f3bf40b6410166d844f73ed4ad09700", "85bc6bdaf9b68d47cf01405d5b9e2e44", "811ad11ae65873adb93f35188aeb336e", "1db3d68b5533061f45263d1f84b5676c", "eb1e930ffcc9bd728bc13d7d7be937f1", "0770a18a50c3e703dee754ee0018ca27", "1d9b9a5fd8e13921d95a52f0c8ca7f1d", "ae64ace2106f106b46903ecc7f971b61", "36526bb291c870addd085e6f54e45012", "e4fd4f5f53de955da1315ca9e8dae3dd", "4997ff8c8ef8f4006bacf9b1e572df4c", "62ced043412571143a349ee56db856c4", "ea2f00f5bd9447329a77e04209ab28ce", "da76a88f237d9e535c9b48830473a89f", "0dcaa28b74fab7e736f6b020da29f552", "a25ef98753c92e49e173d5e5aeaed428", "dc827850cdd1b20d5ed2bfbcea7e27ba", "b1c04aadce9c879b38482b864f112083", "6656836d931c8e09e98b9e5887214664", "9c4b0b5d1daf67acfb062fba0885104f", "720c99121dc875bbcdd1cac751095797", "c14c271c84a62a7fcbffb7de35b93620", "7bb95ef96d5393442415aaa79a65f1fa", "74472bf0673d1e87c191ab1aa66d6eb7", "b89c9e3dadd2e188f1393bf3be8554b1", "e228f40d4cf364eee10cf492286fbb46", "59b505d49ab6b0292e1d4cdb9a2c6553", "b9199783cc9d93dc544a5ecbabbadcbe", "cab5ec6f6acddc7fd73e4489cc5f4f07", "06f886207d8011ed61be229facd2ae17", "bc469cc94c4b47f837c6abcdabd3c9c1", "e02ec69c09b4932dc08d83f9eec955a9", "853b38a0b16ca7c708a20188a32ab590", "4301da2603f14e3fefb9ed13b56d4030", "3b69cb0b2976d78c0a565af12484320f", "a7842e89d95c5ed147e0eb3415a1ddfa", "220e3886045aeb5f1cf1ee16c4c43438", "bcb16d41a30d76d00b50e0561878abe1", "810c76e27c19df459f0910e8e4ae7b3b", "110f4f7f420649d7ff8f7addc441ce95", "d3457e8fe9c52dd18c6b2cfc947cb8e7", "1a4c52e28449f1800992c9404eb3a0a3", "db16ec693ab22ed83fc9c2d15826931b", "975cc8042bb482523071e81dfd800cd1", "1795832b18ec1da793b699137c9fd645", "207bf0999217346ba4cf40cc157203fc", "be06edd1a027edf29e87233743492e54", "1243783e51a33b881d1d8c0a13909981", "46e0509e36b9714fcd17e7270d586452", "070a4bbb4b8167fbea22cf9ebd344f7b", "bfab870f12b7dfb82447e29cf14a8b1a", "9aa5cd9c53e1f9a8be4d9f7a5d8b389d", "fd04a386fd31873019120078204e7088", "65b3e7e1f02c7237e83c8b2572e63e59", "d331116e1cf1da9d03aa7bd50e93f029", "9b902ac303b7b7b60ea35d8f07e668ee", "fb9dc0c24a405eb5e2a44208b1b8af10"]}' http://admin:teste123@104.131.51.202/puzzles/1`