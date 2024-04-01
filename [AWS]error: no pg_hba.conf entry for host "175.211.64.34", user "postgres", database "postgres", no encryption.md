## 문제 : error: no pg_hba.conf entry for host "175.211.64.34", user "postgres", database "postgres", no encryption

```jsx
/Users/osy/Flashback/node_modules/pg-protocol/dist/parser.js:283
const message = name === 'notice' ? new messages_1.NoticeMessage(length, messageValue) : new messages_1.DatabaseError(messageValue, length, name);
^

error: no pg_hba.conf entry for host "175.211.64.34", user "postgres", database "postgres", no encryption
at Parser.parseErrorMessage (/Users/osy/Flashback/node_modules/pg-protocol/dist/parser.js:283:98)
at Parser.handlePacket (/Users/osy/Flashback/node_modules/pg-protocol/dist/parser.js:122:29)
at Parser.parse (/Users/osy/Flashback/node_modules/pg-protocol/dist/parser.js:35:38)
at Socket.<anonymous> (/Users/osy/Flashback/node_modules/pg-protocol/dist/index.js:11:42)
at Socket.emit (node:events:514:28)
at addChunk (node:internal/streams/readable:545:12)
at readableAddChunkPushByteMode (node:internal/streams/readable:495:3)
at Readable.push (node:internal/streams/readable:375:5)
at TCP.onStreamRead (node:internal/stream_base_commons:190:23) {
length: 161,
severity: 'FATAL',
code: '28000',
detail: undefined,
hint: undefined,
position: undefined,
internalPosition: undefined,
internalQuery: undefined,
where: undefined,
schema: undefined,
table: undefined,
column: undefined,
dataType: undefined,
constraint: undefined,
file: 'auth.c',
line: '542',
routine: 'ClientAuthentication'
}

Node.js v20.10.0
```

## 해결

- AWS RDS의 DB 파라미터 그룹을 새로 생성하여 파라미터 중 
`password_encryption` 를 “MD5”로 수정함.