---
id: licensing-and-subscription
url: annotation/python-net/licensing-and-subscription
title: Licensing and evaluation
weight: 5
keywords: free, free trial, subscription, evaluation, watermark, metered, groupdocs annotation python
description: "GroupDocs.Annotation for Python via .NET offers flexible licensing options, including evaluation mode and a 30-day Temporary License for evaluation purposes."
productName: GroupDocs.Annotation for Python via .NET
hideChildren: False
toc: True
---

To explore the system effectively, you may want immediate access to the API. GroupDocs.Annotation simplifies this by offering various purchase plans, along with an evaluation mode and a 30-day Temporary License for evaluation.

{{< alert style="info" >}}

To learn more about licensing options, purchasing, and evaluation policies, refer to the [Purchase Policies and FAQ](https://purchase.groupdocs.com/policies) section.

{{< /alert >}}

## Purchased License

After purchasing GroupDocs.Annotation for Python via .NET, you will receive a license file that unlocks the full functionality of the API. A few rules apply:

- Apply the license **only once** per process, in your start-up code.
- Apply it **before** constructing any `Annotator` or other GroupDocs.Annotation object.
- A license can be applied from a file path, from a binary stream (handy when the license is an embedded resource), or as a [Metered License](https://purchase.groupdocs.com/faqs/licensing/metered/) that bills by usage.

Use the [set_license](https://reference.groupdocs.com/annotation/python-net/groupdocs.annotation/license/set_license/) method to license the component. Calling it more than once is harmless — it simply wastes a little processor time.

### Set a license from a file

The example below applies a license from a file path. It reads the path from the `GROUPDOCS_LIC_PATH` environment variable and falls back to a local `GroupDocs.Annotation.lic` file:

{{< tabs "code-example-set-license-from-file" >}}
{{< tab "set_license_from_file.py" >}}
```python
import os
from groupdocs.annotation import License

def set_license_from_file():
    # Resolve the license path from the environment, with a local fallback
    license_path = os.environ.get("GROUPDOCS_LIC_PATH", "./GroupDocs.Annotation.lic")

    # Apply the license before using any annotation features
    if os.path.exists(license_path):
        License().set_license(license_path=license_path)
        print("License set successfully.")
    else:
        print("License file not found. Running in evaluation mode.")

if __name__ == "__main__":
    set_license_from_file()
```
{{< /tab >}}
{{< /tabs >}}

### Set a license from a stream

You can also apply a license from any readable binary stream — useful when the license ships as an embedded resource:

{{< tabs "code-example-set-license-from-stream" >}}
{{< tab "set_license_from_stream.py" >}}
```python
import os
from groupdocs.annotation import License

def set_license_from_stream():
    # Resolve the license path from the environment, with a local fallback
    license_path = os.environ.get("GROUPDOCS_LIC_PATH", "./GroupDocs.Annotation.lic")

    # Apply the license from an open binary stream
    if os.path.exists(license_path):
        with open(license_path, "rb") as license_stream:
            License().set_license(license_stream=license_stream)
        print("License set successfully from stream.")
    else:
        print("License file not found. Running in evaluation mode.")

if __name__ == "__main__":
    set_license_from_stream()
```
{{< /tab >}}
{{< /tabs >}}

### Set a metered license

A Metered License lets you pay for what you use. Set the public and private keys with [set_metered_key](https://reference.groupdocs.com/annotation/python-net/groupdocs.annotation/metered/set_metered_key/) before using the API, then query consumption at any time:

{{< tabs "code-example-set-metered-license" >}}
{{< tab "set_metered_license.py" >}}
```python
import os
from groupdocs.annotation import Metered

def set_metered_license():
    # Read the metered public and private keys from the environment
    public_key = os.environ.get("GROUPDOCS_METERED_PUBLIC_KEY", "")
    private_key = os.environ.get("GROUPDOCS_METERED_PRIVATE_KEY", "")

    # Apply the metered keys before using any annotation features
    if public_key and private_key:
        metered = Metered()
        metered.set_metered_key(public_key=public_key, private_key=private_key)
        print("Metered license set successfully.")

        # Query the current metered consumption
        print(f"Consumption quantity: {Metered.get_consumption_quantity()}")
        print(f"Consumption credit: {Metered.get_consumption_credit()}")
    else:
        print("Metered keys not provided. Running in evaluation mode.")

if __name__ == "__main__":
    set_metered_license()
```
{{< /tab >}}
{{< /tabs >}}

### Changing the license file name

You are not required to keep the license file name as `GroupDocs.Annotation.lic`. You can rename it to any preferred name and use that name when applying the license in your application.

### "Cannot find license filename" exception

When you download the license from the GroupDocs website it is saved as `GroupDocs.Annotation.lic`. However, some web browsers may automatically append `.xml`, resulting in `GroupDocs.Annotation.lic.xml`.

If your Windows settings are configured to hide file extensions (the default), the file may still appear as `GroupDocs.Annotation.lic` in File Explorer even though the actual name is `GroupDocs.Annotation.lic.xml`. This discrepancy can cause `set_license` to throw an exception. To fix it, manually rename the file to remove the `.xml` extension, or disable "Hide extensions for known file types" in Windows.

## How to evaluate GroupDocs.Annotation

You can evaluate GroupDocs.Annotation for Python via .NET without purchasing a license. The evaluation version is identical to the purchased one; it becomes fully licensed once you set a license.

### Evaluation mode

Without a license, GroupDocs.Annotation runs in evaluation mode:

- The API is **fully functional** — you can open documents, add, get, update, and remove annotations, and save the result. Every operation completes successfully and no exception is thrown.
- There is **no limit** on the number of documents you can open in a process and **no cap** on the number of annotations you can add. You can run as many `Annotator` operations as you like, one after another, in the same process.
- An **evaluation watermark** is added to the output document, so the saved file is slightly larger than a licensed one.

To remove the evaluation watermark, apply a purchased or temporary license as shown above.

### Temporary License

To produce output without the evaluation watermark while you assess the full features of GroupDocs.Annotation, you can request a 30-day ["Temporary License"](https://purchase.groupdocs.com/temporary-license).
</content>
</invoke>
