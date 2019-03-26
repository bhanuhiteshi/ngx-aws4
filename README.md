ng-aws4
----
An utility to sign http(s) request options using Amazon's
[AWS Signature Version 4](http://docs.amazonwebservices.com/general/latest/gr/signature-version-4.html).

Installation
------------

With [npm](http://npmjs.org/) do:

```
npm install ng-aws4
```


Example
-------

```javascript
import * as aws4 from "ng-aws4";

...

public static getAWS4Signature(url, path) {
	let requestOptions: any = {
		host: `${AWSCredentials.AWS_STS.BUCKET_NAME}.s3.${AWSCredentials.AWS_STS.REGION}.amazonaws.com`,
		path: path
	}

	console.log(aws4);

	aws4.sign(requestOptions, {
		secretAccessKey: AWSCredentials.AWS_STS.SECRET_KEY,
		accessKeyId: AWSCredentials.AWS_STS.ACCESS_KEY,
		sessionToken: AWSCredentials.AWS_STS.SESSION_TOKEN
	})
	console.log(requestOptions);

	return requestOptions;
}

...

```

More options
------------

```javascript
// you can also pass AWS credentials in explicitly (otherwise taken from process.env)
aws4.sign(opts, {accessKeyId: '', secretAccessKey: ''})

// can also add the signature to query strings
aws4.sign({service: 's3', path: '/my-bucket?X-Amz-Expires=12345', signQuery: true})
```

Thanks
------

Thanks to [@mhart](https://github.com/mhart/aws4)

Thanks to [@jed](https://github.com/jed) 

Also thanks to the
[official node.js AWS SDK](https://github.com/aws/aws-sdk-js) 

