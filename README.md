# lambda-function-wrapper-ruby

Run Ruby from [AWS Lambda](http://docs.aws.amazon.com/lambda/latest/dg/lambda-introduction.html). Just a proof of concept, but it works!

Here's the logs from Lambda:

```
Logs
----
START RequestId: 13836895-7132-11e4-8f05-ebd8b45899f3
2014-11-21T03:54:21.120Z	13836895-7132-11e4-8f05-ebd8b45899f3	stdout:
Testing Ruby!

2014-11-21T03:54:21.181Z	13836895-7132-11e4-8f05-ebd8b45899f3	stdout:
Hello, Lambda from Ruby!

END RequestId: 13836895-7132-11e4-8f05-ebd8b45899f3
REPORT RequestId: 13836895-7132-11e4-8f05-ebd8b45899f3	Duration: 281.39 ms	Billed Duration: 300 ms 	Memory Size: 128 MB	Max Memory Used: 10 MB	

Message
-------
undefined
```

## How?

Actually it's [mruby](https://github.com/mruby/mruby), not Ruby. I'd bet Ruby would work too but the payload for the binary would be bigger.

* Lambda invokes a node.js function of your choosing
* That node function (`lambda-function-wrapper.js`) runs a bash script (`lambda-function`)
* Bash script then executes the `mruby` binary. (Compiled on DigitalOcean since I was too lazy to boot an EC2 instance)

This is probably more convoluted than it needs to be, but who cares!

## Credits

* https://github.com/alestic/lambda-function-wrapper
* http://alestic.com/2014/11/aws-lambda-environment
