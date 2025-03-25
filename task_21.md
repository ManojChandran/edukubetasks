# Create a cronjob which prints the date and "Running" every minute
### Manifest file 
```yaml
apiVersion: batch/v1
kind: CronJob
metadata:
  name: print-date-job
spec:
  schedule: "*/1 * * * *"  # Runs every minute
  jobTemplate:
    spec:
      template:
        spec:
          containers:
          - name: print-date
            image: busybox
            command: ["/bin/sh", "-c", "date; echo Running"]
          restartPolicy: OnFailure
```
### Apply the CronJob to the cluster using:
```
kubectl apply -f cronjob.yaml
```
### Verify the CronJob using:
```
kubectl get cronjob
```
### Check the completed jobs with:
```
kubectl get jobs
```
### Check logs of the latest job's pod:
``` 
kubectl logs print-date-job-29047797
```
### Pause a CronJob, patch it with suspend: true:
```
kubectl patch cronjob print-date-job -p '{"spec": {"suspend": true}}'
```
### Resume the suspended JOB
```
kubectl patch cronjob print-date-job -p '{"spec": {"suspend": false}}'
```
### Check the JOB status
```
kubectl get cronjob print-date-job -o yaml | grep suspend
```