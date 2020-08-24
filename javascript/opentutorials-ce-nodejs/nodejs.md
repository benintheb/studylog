# WEB2 - Node.js

[course](https://opentutorials.org/course/3332) from opentutorials

---

## 

---

## URL

<img src="https://code-boxx.com/wp-content/uploads/2018/06/js-url-parts-r2.jpg" alt="url-parts" width="70%">

- The red part is the protocol. It defines how a client is going to communicate with the server.  
HTTP is short for HyperText Transfer Protocol. It's a protocol to transfer data in the web.

- The green part is the domain name. Also called as a host. It is to recognize a computer on the network on a wider scale.  
On a narrower(more widely used) scale, it is a name that is registered from a domain registry.

- The pink part is the port. A port is like a docking station for a computer to connect to services and programs on the Internet.  
It is a way that a client connects to a server.  
Well known ports such as the Web protocol and the Hypertext Transfer Protocol are given preassigned numbers for their ports. Other programs are given ports dynamically for connections.

- The blue part is the path, it leads the client to the directory of the file inquired.

- The turquoise part is the query string. The query string assigns values to specified parameters.  
Through the query string a client can send data over to the web server.  
Query strings start with `?`, and uses `&` between values. A value and its name are linked with `=`.

---

## fs Module

### fs.readFile(file[, options], callback)

`readFile` is an asyncronous way to read a file. `file` is read in `options` format and sent to `callback`.

    fs.readFile('sample.txt', 'utf8', function(err, data){
        if (err) throw err;
        console.log(data);
    });

### fs.readFileSync(file[, options])

`readFileSync` is a syncronous version of `readFile`. It returns the contents of a file syncronously. 

    var data = fs.readFileSync('sample.txt', 'utf8');
    console.log(data);

- For both `readFile` and `readFileSync`, should the function return a string, the `encoding` option is specified on the `options` part.

### fs.readdir(path[, options], callback)

`readdir` is a way to read the contents of a directory. The method requires a path to the directory, and executes a callback function. The callback gets two arguments, `(err, files)` where files is an array of the file names in the inquired directory.

There is a synchronous way of `readdir`, which is `fs.readdirSync(path[, options])`