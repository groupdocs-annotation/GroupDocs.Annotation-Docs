---
id: licensing-and-subscription
url: annotation/net/licensing-and-subscription
title: Licensing
weight: 5
description: "GroupDocs.Viewer provides different plans for purchasing or offers a Free Trial and a 30-day Temporary License for evaluation."
keywords: free, free trial, evaluation, groupdocs.annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
toc: True
---
Sometimes, to study the system better, you want to dive into the code as fast as possible. To make this easier, GroupDocs.Annotation provides different plans for purchase or offers a Free Trial and a 30-day Temporary License for evaluation.

{{< alert style="info" >}}

Note that there are a number of general policies and practices that guide you on how to evaluate, properly license, and purchase our products. You can find them in the ["Purchase Policies and FAQ"](https://purchase.groupdocs.com/policies) section.

{{< /alert >}}

## Free Trial or Temporary License

You can try GroupDocs.Annotation without buying a license.

### Free Trial

The evaluation version is the same as the purchased one – the evaluation version simply becomes licensed when you set the license. You can set the license in a number of ways that described in the next sections of this article.

The evaluation version comes with the limitations:

- Only first 2 pages can be processed.
- Trial badges are placed in the document on the top of each page.

### Temporary License

If you wish to test GroupDocs.Annotation without the limitations of the trial version, you can also request a 30-day Temporary License. For details, see the ["Get a Temporary License"](https://purchase.groupdocs.com/temporary-license) page.

## How to set a license

{{< alert style="info" >}}

You can find the pricing information on the ["Pricing Information"](https://purchase.groupdocs.com/pricing/annotation/net) page.

{{< /alert >}}

After getting the license, you need to set it. This section describes different ways to set the license.

The license should be set:

- Only once per application domain.
- Before using any other of GroupDocs.Annotation classes.

{{< alert style="info" >}}

The license can be set multiple times per app domain but we recommend doing it once since all calls to `SetLicense` except first will just waste processor time.

{{< /alert >}}

### Set License from File

The following code snippet shows how to set a license from file:

{{< tabs "example1">}}
{{< tab "C#" >}}

```csharp
string licensePath = "path to the .lic file";
License license = new License();
license.SetLicense(licensePath);
```

{{< /tab >}}
{{< /tabs >}}


### Set License from Stream

The following code snippet shows how to set a license from a stream:

{{< tabs "example2">}}
{{< tab "C#" >}}

```csharp
string licensePath = "path to the .lic file";
using (FileStream fileStream = File.OpenRead(licensePath))
{
    License license = new License();
    license.SetLicense(fileStream);
}
```

{{< /tab >}}
{{< /tabs >}}


### Set Metered License

You can also set the [Metered](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/metered/) license as an alternative to license file. It is a new licensing mechanism that will be used along with existing licensing method. It is useful for the customers who want to be billed based on the usage of the API features. For  details, please refer to the [Metered Licensing FAQ](https://purchase.groupdocs.com/faqs/licensing/metered) section.

The following code snippet shows how to use `Metered` licensing:

{{< tabs "example3">}}
{{< tab "C#" >}}

```csharp
string publicKey = ""; // Your public license key
string privateKey = ""; // Your private license key

Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);

// Get amount (MB) consumed
decimal amountConsumed = GroupDocs.Viewer.Metered.GetConsumptionQuantity();
Console.WriteLine("Amount (MB) consumed: " + amountConsumed);

// Get count of credits consumed
decimal creditsConsumed = GroupDocs.Viewer.Metered.GetConsumptionCredit();
Console.WriteLine("Credits consumed: " + creditsConsumed);
```

{{< /tab >}}
{{< /tabs >}}