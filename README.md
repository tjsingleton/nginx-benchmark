# Nginx Benchmark

## Results

### No rewrite

`siege http://nginx-benchmark.vagrant.vm/ -b -t 1m`

```
Transactions:		       47396 hits
Availability:		      100.00 %
Elapsed time:		       59.69 secs
Data transferred:	        5.65 MB
Response time:		        0.02 secs
Transaction rate:	      794.04 trans/sec
Throughput:		        0.09 MB/sec
Concurrency:		       14.43
Successful transactions:       47397
Failed transactions:	           0
Longest transaction:	        0.72
Shortest transaction:	        0.00
```

### With rewrite redirect

`siege http://nginx-benchmark.vagrant.vm/rewrite/ohai -b -t 1m`

```
Transactions:		       55584 hits
Availability:		      100.00 %
Elapsed time:		       59.61 secs
Data transferred:	        7.58 MB
Response time:		        0.02 secs
Transaction rate:	      932.46 trans/sec
Throughput:		        0.13 MB/sec
Concurrency:		       14.09
Successful transactions:       55595
Failed transactions:	           0
Longest transaction:	        0.75
Shortest transaction:	        0.00
```

## How to test

1. [Install vagrant](https://www.vagrantup.com/downloads.html)
2. Install the hostmanager plugin: `vagrant plugin install vagrant-hostmanager`
3. Start the virtual machine: `vagrant up`
4. Benchmark with your tool of choice. I used [siege](https://www.joedog.org/siege-home/). 

The hostname is http://nginx-benchmark.vagrant.vm. http://nginx-benchmark.vagrant.vm/rewrite/* will be redirected to http://nginx-benchmark.vagrant.vm/?path=*. 

You can modify the configuration in `nginx/example.conf`. To reload, run `vagrant provision`. Nginx logs are available at `/var/log/nginx`.