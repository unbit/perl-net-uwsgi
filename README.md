Net::uwsgi
==========

perl module for easy interaction with uWSGI servers or for manipulating uwsgi packets


Synopsys
--------

```perl

   use Net::uwsgi;
   
   # call rpc function 'hello' passing 'roberta' and 'serena' as args
   print uwsgi_rpc('ubuntu64.local:3031', 'hello', 'roberta', 'serena')."\n";
   
   # raise uwsgi signal 17
   uwsgi_signal('ubuntu64.local:3031', 17);
   
   # get the '/etc/passwd' item from the cache named 'pippo'
   print uwsgi_cache_get('pippo@ubuntu64.local:3031', '/etc/passwd');
   
   # get the 'foobar' item from the default cache
   print uwsgi_cache_get('ubuntu64.local:3031', 'foobar');
   
   # the same but using unix sockets
   print uwsgi_cache_get('/tmp/uwsgi.socket', 'foobar');
   
   # update the cache
   uwsgi_cache_update('pippo@ubuntu64.local:3031', 'test', 'test001');
   
   # set a cache item (will fail as 'set' does not update already existent items)
   uwsgi_cache_set('pippo@ubuntu64.local:3031', 'test', 'test001');
   
   # delete a cache item
   uwsgi_cache_del('pippo@ubuntu64.local:3031', 'test')
   
   # fast check if an item exists
   if (uwsgi_cache_exists('pippo@ubuntu64.local:3031', 'test')) {
           print "all fine here\n";
   }
   
   # spool a request in the uwsgi spooler
   uwsgi_spool('ubuntu64.local:3031', {'test'=>'test001','argh'=>'boh','foo'=>'bar'});
```
