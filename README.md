# s3-buckets-bruteforcer
PHP tool to brute force Amazon S3 bucket  
Note that this is an automated tool, manual check is still required.  

```
Usage: php s3-buckets-bruteforcer.php [OPTIONS] --bucket <bucket>

Options:
	--bucket	single bucket name or listing file
	--force-recurse	even if the bucket doesn't exist, the max-depth option will be applied (use this option at your own risk)
	--glue		characters used as a separator when concatenate all elements, default are: dot, dash and underscore
	-h, --help	print this help
	--list		do no perform any test, simply list the generated permutations
	--max-depth	max depth of recursion, if a bucket is found, another level will be added (permutations are applied), default=1, ex:
				if <bucket> is found then test <bucket>-xxx
				if <bucket>-xxx is found then test <bucket>-xxx-yyy
	--no-color	disable colored output
	--perform	tests to perform, default=esglw
				e: test if exist (always performed)
				s: set ACL
				g: get ACL
				l: list (cli and http)
				w: write
	--permut	permutation can be tested, default=0
				0: no permutation
				1: if both provided prefix and suffix are permuted (prefix.<bucket>.suffix, suffix.<bucket>.prefix)
				2: permutation applied only on the bucket name (a.b.c, b.c.a, ...)
				3: each elements will be separately permuted, then glogal permutation
	--prefix	single prefix or listing file
	--region	set the region, value can be:
				us-east-1, us-east-2, us-west-1, us-west-2,
				ap-south-1, ap-northeast-2, ap-southeast-1, ap-southeast-2, ap-northeast-1,
				eu-central-1, eu-west-1, eu-west-2,
				ca-central-1, sa-east-1
	--suffix	single suffix or listing file
	--thread	max threads, default=5
	-v,--verbosity	set verbosity, default=0
				0: everything
				1: do not display not found
				2: display only permissions success
				3: display only set ACL and write permission success

Examples:
	php s3-buckets-bruteforcer.php --bucket gwen001-test002
	php s3-buckets-bruteforcer.php --bucket listing.txt --no-color --verbosity 1
	php s3-buckets-bruteforcer.php --bucket listing1.txt --bucket listing2.txt --bucket listing3.txt --perform e --thread 10
	php s3-buckets-bruteforcer.php --bucket listing.txt --prefix prefix.txt --suffix suffix1.txt --suffix2.txt --perform esw --thread 10
	php s3-buckets-bruteforcer.php --bucket listing.txt --region us-east-2 --rlevel 3
```

I don't believe in license.  
You can do want you want with this program.  
