---

copyright:
  years: 2024
lastupdated: "2024-12-10"

---

{{site.data.keyword.attribute-definition-list}}

# Installing the {{site.data.keyword.powerSys_notm}} CLI plug-in
{: #power-iaas-cli-byb}

---

{{site.data.keyword.off-prem-fname}} in [{{site.data.keyword.off-prem}}]{: tag-blue}

{{site.data.keyword.on-prem-fname}} in [{{site.data.keyword.on-prem}}]{: tag-red}

---



To install, update, or view the {{site.data.keyword.powerSys_notm}} CLI plug-in, complete the following steps:

1. Install the [{{site.data.keyword.cloud}} CLI](https://cloud.ibm.com/docs/cli?topic=cloud-cli-getting-started){: external}.

2. Install or update the `power-iaas` plug-in.

    **To install:**

    ```bash
    ibmcloud plugin install power-iaas
    ```

    **To update:**

    ```bash
    ibmcloud plugin update
    ```

    **To view your installed plug-ins and versions:**

    ```bash
    ibmcloud plugin list
    ```

3. Log in to the [{{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/login){: external}.

    The power-iaas command-line plug-in uses the region that `ibmcloud login` targets to determine the {{site.data.keyword.powerSys_notm}} endpoint. For example, to use the {{site.data.keyword.powerSys_notm}} endpoint `https://cloud.ibm.com` you must use the `ibmcloud login -a https://cloud.ibm.com` command to target the `us-east` region. If you have a federated account, use the following command:

    ```bash
    ibmcloud login -a https://cloud.ibm.com -sso
    ```

4. Run one of the following commands to list all the services under your account:

   * For IBM {{site.data.keyword.powerSys_notm}} in {{site.data.keyword.off-prem}}, run the `ibmcloud pi ws ls` command.
     The **Cloud Resource Name** (CRN) under **ID** contains your **Tenant ID** and **Cloud Instance ID**. The following example shows a typical CRN:

    ```screen
    crn:v1:staging:public:power-iaas:us-east:a/abcdefghijklmnopqrstuvwxyzabcdef:121d5ee5-b87d-4a0e-86b8-aaff422135478::
    ```

   * For {{site.data.keyword.on-prem-fname}} in {{site.data.keyword.on-prem}}, run the `ibmcloud pi ws ls -p` command.

5. Target your service by entering one of the following commands:
   * For IBM {{site.data.keyword.powerSys_notm}} in {{site.data.keyword.off-prem}}, enter `ibmcloud pi ws tg <CRN>` command.
   * For {{site.data.keyword.on-prem-fname}} in {{site.data.keyword.on-prem}}, enter `ibmcloud pi ws tg satloc_*`

    The following is an example of the output when you enter `ibmcloud pi ws tg <CRN>` command:

    ```bash
    ibmcloud pi ws tg crn:v1:staging:public:power-iaas:us-east:a/abcdefghijklmnopqrstuvwxyzabcdef:121d5ee5-b87d-4a0e-86b8-aaff422135478::
    ```

Power Systems Virtual Server CLI requires a valid IAM token authorization before each use. Use the ibmcloud login command to renew authorization if your token expires.
{: note}
