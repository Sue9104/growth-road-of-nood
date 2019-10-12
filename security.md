# Security

## OSI Model

OSI provides standard for different computer systems to be able to communicate 
with each other.

1. Physical layer
2. Datalink layer: define data format
3. Network layer: packet routing
4. Transport layer: UDP TCP
5. Session layer: aviod data waste
6. Presentation layer: translation, encrypt, compression
7. Application layer: HTTP, SMTP

## HTTP vs HTTPS

<table>
  <tr>
    <th></th>
    <th>HTTP</th>
    <th>HTTPS (HTTP + SSL/TLS)</th>
  </tr>
  <tr>
    <td>port</td>
    <td>80</td>
    <td>443</td>
  </tr>
  <tr>
    <td>Drawback</td>
    <td>Clear Text & No Log out</td>
    <td>
      <ul>
        <li>Fees for CA</li>
        <li>Establish slowly than HTTP</li>
        <li>More computer resources</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>Connect</td>
    <td>
      TCP 3-way Handshake
      <ol>
        <li>Client send syn: SYN_SEND</li>
        <li>Server receive syn and send syn+ack: SYN_RECV</li>
        <li>Client receive syn+ack send ack: ESTABLISHED</li>
      </ol>
    </td>
    <td>
      <ol>
        <li>Client send request: </li>
        <li>Server generate server publish key and private key</li>
        <li>Server send own publish key</li>
        <li>Client encrypt random number with server publish key</li>
        <li>Client send the encrypted key</li>
        <li>Server decrypts the key with own private key and encrypts content with key</li>
        <li>Server send encrypted content</li>
        <li>Client encrypt the content with own private key</li>
      </ol>
    </td>
  </tr>
</table>

## API security

1. expired certification
2. signature certification
3. replay attacks: timestamp + nonce
4. request limit: an arrest in spike traffic or a per-app usage quota
5. sql injections
6. sensitive data in the open: encryption and data masking

### SQL injections

1. control database permission: role, table, revise permission
2. check input format
3. escape special characters
4. use database parametric query
5. precompile
6. use tools to check injections before release
7. do not print database error log

## Sign up

### session

登录成功后，保存session id到cookie中，再次请求时server检查session id是否在数据库中。

缺点：
- 没有分布式架构,无法实现横向扩展
- 适用于web环境，本地cookie容易被劫持，不安全
- 数据库资源消耗大，速度相对较慢

### token

登录成功的token放在Header或URL中，Server直接验证无需调用数据库。

缺点：
- 无法保存session状态，一旦签发，一定期限内会一直有效
- 一旦泄露，任何人将会获得该token的所有权限

#### Oauth

牵扯应用信息的访问授权，也可作身份验证。

- 用户授权后，得到access code
- 用access code获得access token
- 用access token获取资源

OpenID则无法访问其他应用信息，只做身份验证

#### JWT

身份认证

- 用私钥和client ID创建一个签名的JWT
- server发回access token
- 用access token 获取资源

