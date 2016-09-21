# gojob
Resque jobs triggering package

Use it to trigger job from any golang application:

```
jobWithStatus := gojob.Job{
		Queue: "emails",
		Payload: gojob.Payload{
			Class: "Jobs::SendEmail",
			Args: []interface{}{
				"Status-UUID",
				params,
			},
		},
	}

// To track job's status via resque-status plugin https://github.com/quirkey/resque-status
gojob.EnqueueWithStatus(&jobWithStatus)

// To trigger regular resque's jobs
gojob.Enqueue(&jobWithStatus)
```

Not production ready yet, just a POC
