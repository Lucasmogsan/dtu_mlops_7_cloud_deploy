# dtu_mlops_7_cloud_deploy

1. Build

```bash
docker build -f dockerfiles/simple_fastapi_app.dockerfile . -t gcp_test_app:latest
```

2. Tag and push

```bash
docker tag gcp_test_app gcr.io/<project-id>/gcp_test_app
docker push gcr.io/<project-id>/gcp_test_app
```

```bash
docker tag gcp_test_app gcr.io/nifty-byway-410709/gcp_test_app
docker push gcr.io/nifty-byway-410709/gcp_test_app
```

3. Deploy from gcp
- Follow steps from mlops course
- cml approach:
```bash
gcloud run deploy $APP --image $TAG --platform managed --region $REGION --allow-unauthenticated
```

```bash
gcloud run deploy cli-simple-app --image gcr.io/nifty-byway-410709/gcp_test_app --platform managed --region europe-west6 --allow-unauthenticated
```

4. Verify

```bash
gcloud run services list
```

```bash
gcloud run services describe cli-simple-app --region europe-west6
```