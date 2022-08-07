# gcp-landing-zone
Google Cloud Landing Zone using Java IaC

# Developer Guide
- Refer to https://cloud.google.com/java/docs/reference
- https://cloud.google.com/storage/docs/reference/libraries#client-libraries-install-java
- https://github.com/googleapis/google-cloud-java

# Running the CLI
```
michael@cloudshell:~/github/cloud-quickstart/gcp-landing-zone (lz-stg)$ mvn clean install -U
michael@cloudshell:~/github/cloud-quickstart/gcp-landing-zone (lz-stg)$ java -jar gcp-landing-zone-deploy/target/gcp-landing-zone-deploy-0.0.1-SNAPSHOT.jar zone.gcp.landing.Cli
S
```
## Create your bootstrap Google Cloud project
```
michael@cloudshell:~$ gcloud projects create gcp-zone-landing-stg --name="gcp-zone-landing-stg" --labels=type=dev
Create in progress for [https://cloudresourcemanager.googleapis.com/v1/projects/gcp-zone-landing-stg].
Waiting for [operations/cp.6078773111587977724] to finish...done.    
Enabling service [cloudapis.googleapis.com] on project [gcp-zone-landing-stg]...
Operation "operations/acat.p2-1017366855021-820d71c9-a8f2-4d3c-a3ad-8d877176d5a8" finished successfully.
michael@cloudshell:~$ git config --global user.email "michael@"
michael@cloudshell:~$ git config --global user.name "Michael"
michael@cloudshell:~$ git clone https://github.com/cloud-quickstart/gcp-landing-zone.git
Username for 'https://github.com': obrien...
Password for 'https://obriensystems@github.com': use your auth token
michael@cloudshell:~/cloud-quickstart$ gcloud config set project gcp-zone-landing-stg
michael@cloudshell:~/cloud-quickstart (gcp-zone-landing-stg)$
```

Get default enabled services
```
michael@cloudshell:~/cloud-quickstart (gcp-zone-landing-stg)$ gcloud services list --enabled --project gcp-zone-landing-stg | grep NAME
NAME: bigquery.googleapis.com
NAME: bigquerymigration.googleapis.com
NAME: bigquerystorage.googleapis.com
NAME: cloudapis.googleapis.com
NAME: clouddebugger.googleapis.com
NAME: cloudtrace.googleapis.com
NAME: datastore.googleapis.com
NAME: logging.googleapis.com
NAME: monitoring.googleapis.com
NAME: servicemanagement.googleapis.com
NAME: serviceusage.googleapis.com
NAME: sql-component.googleapis.com
NAME: storage-api.googleapis.com
NAME: storage-component.googleapis.com
NAME: storage.googleapis.com
```

Enable compute for VPC creation
```
michael@cloudshell:~ (lz-stg)$ gcloud services enable compute.googleapis.com
Operation "operations/acf.p2-918623670639-494fcadb-4df0-43e9-b778-835bea73645b" finished successfully.
```

## Add the GCP SDK to your maven project
- examples:  https://cloud.google.com/docs/samples/?q=enable+service&l=java
- Add the dependency in your pom
- https://github.com/googleapis/google-cloud-java/tree/monorepo_script_output/java-service-control
- https://cloud.google.com/iam/docs/samples/iam-quickstart#iam_quickstart-java
- https://github.com/GoogleCloudPlatform/java-docs-samples/blob/HEAD/iam/api-client/src/main/java/iam/snippets/Quickstart.java
```
<dependency>
  <groupId>com.google.cloud</groupId>
  <artifactId>google-cloud-service-control</artifactId>
  <version>1.3.0</version>
</dependency
```


