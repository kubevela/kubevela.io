---
title: vela provider add terraform-alibaba
---

Authenticate Terraform Cloud Provider terraform-alibaba

### Synopsis

Authenticate Terraform Cloud Provider terraform-alibaba by creating a credential secret and a Terraform Controller Provider

```
vela provider add terraform-alibaba [flags]
```

### Examples

```
vela provider add terraform-alibaba
```

### Options

```
      --ALICLOUD_ACCESS_KEY string   Get ALICLOUD_ACCESS_KEY per this guide https://help.aliyun.com/knowledge_detail/38738.html
      --ALICLOUD_REGION string       Get ALICLOUD_REGION by picking one RegionId from Alibaba Cloud region list https://www.alibabacloud.com/help/doc-detail/72379.htm
      --ALICLOUD_SECRET_KEY string   Get ALICLOUD_SECRET_KEY per this guide https://help.aliyun.com/knowledge_detail/38738.html
  -h, --help                         help for terraform-alibaba
      --name default                 The name of Terraform Provider for Alibaba Cloud, default is default (default "default")
```

### Options inherited from parent commands

```
  -y, --yes   Assume yes for all user prompts
```

### SEE ALSO

* [vela provider add](vela_provider_add)	 - Authenticate Terraform Cloud Provider

#### Go Back to [CLI Commands](vela) Homepage.


###### Auto generated by spf13/cobra on 19-Apr-2022, refer to [script in KubeVela](https://github.com/kubevela/kubevela/tree/master/hack/docgen).