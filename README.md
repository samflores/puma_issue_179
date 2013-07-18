A small application that reproduces the issue [#179](https://github.com/puma/puma/issues/179) of Puma server.

The issue only happens when I `require 'rugged'`.

### Steps to reproduce

1. `bundle install`
2. `bundle exec ruby app.rb -s puma`
3. Request `http://localhost:4567/`. I tried with a browser and with `wget` with the same result:

```shell
$ bundle install
$ bundle exec ruby app.rb -s puma
Puma 2.3.2 starting...
* Min threads: 0, max threads: 16
* Environment: development
* Listening on tcp://localhost:4567
== Sinatra/1.4.3 has taken the stage on 4567 for development with backup from Puma
2013-07-18 12:53:33 -0300: HTTP parse error, malformed request (): #<Puma::HttpParserError: HTTP element HEADER is longer than the (1024 * (80 + 32)) allowed length.>
2013-07-18 12:53:33 -0300: ENV: {"rack.version"=>[1, 2], "rack.errors"=>#<IO:<STDERR>>, "rack.multithread"=>true, "rack.multiprocess"=>false, "rack.run_once"=>false, "SCRIPT_NAME"=>"", "CONTENT_TYPE"=>"text/plain", "QUERY_STRING"=>"", "SERVER_PROTOCOL"=>"HTTP/1.1", "SERVER_SOFTWARE"=>"2.3.2", "GATEWAY_INTERFACE"=>"CGI/1.2"}
---
```
