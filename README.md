# gojob
Resque jobs triggering package

## Motivation

Following SRP this package provides only 1 function - triggering jobs in resque. It allows you to reduce amount of dependecies and makes that simpler than goworker package.

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
