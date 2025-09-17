[#]: subject: "Introducing complyctl for Effortless Compliance in Fedora"
[#]: via: "https://fedoramagazine.org/effortless-flexible-scalable-and-standardized-compliance-checks-for-fedora-using-complyctl/"
[#]: author: "Marcus Burghardt https://fedoramagazine.org/author/marcusburghardt/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Introducing complyctl for Effortless Compliance in Fedora
======

![][1]

Photo by [Jei Lee][2] on [Unsplash][3] (rotated)

_complyctl_ is a powerful command-line utility implementing the principles of “ComplianceAsCode” (CaC) with high scalability and adaptability for security compliance.

In today’s rapidly evolving digital landscape, maintaining a robust security posture isn’t just a best practice – it is a necessity. For Fedora users, system administrators, and developers, ensuring that your systems meet various security and regulatory requirements can often feel like a daunting, manual task. But what if you could standardize and automate much of this process, making compliance checks faster, easier to audit, and seamlessly integrated into your workflows?

This is now a reality enabled with multiple [ComplyTime][4] projects. These focus on specific tasks designed to be easily integrated. They allow a robust, flexible, and scalable combination of microservices communicating with standardized formats that ultimately allow a powerful capability to much more easily adapt to the compliance demands. This also allow faster adoption of new technologies. There are multiple exciting projects actively and quickly evolving under the umbrella of [ComplyTime][4] organization. In this article I would like to highlight [complyctl][5], the ComplyTime CLI for Fedora, and its main features that make it an excellent option to easily maintain a robust security posture in your Fedora systems.

_complyctl_ is a powerful command-line utility available since Fedora 42. It’s design uses the principles of “ComplianceAsCode” (CaC) with high scalability and adaptability. It contains a technology agnostic core and is easily extended with plugins. This allows users to use the best of every available underlying technology with a simple and standardized user interface.

### The Power of ComplianceAsCode with complyctl

At its heart, _complyctl_ is a tool for performing compliance assessment activities, scaled by a flexible plugin system that allows users to perform compliance check activities with a flexible combination of the best available assessment technologies.

The _complyclt_ plugin architecture allows quick adoption and combination of different scanner technologies. The core design is technology agnostic with standardizing inputs and outputs using machine readable formats that allow high reusability and shareability of compliance artifacts. Currently it leverages the [Open Security Controls Assessment Language (OSCAL)][6] and its anti-fragile architecture also allows a smooth adoption of future standards, making it a reliable and continuous modern solution for the long-term.

This might sound technical, but the benefits are simple:

  1. **Automation and Speed:** Traditional compliance audits can be slow, manual, complex and prone to human error. _complyctl_ relies on standardized machine readable formats, allowing automation without technology or vendor lock-in.
  2. **Accuracy and Consistency:** Machines are inherently more consistent than human reviewers. _complyctl’s_ reliance on OSCAL provides a standardized format for expressing security controls, assessment plans, and results. This standarization is crucial for interoperability. It allows consistent processing and understanding of compliance data across different tools and systems.
  3. **Scalability and Integration:** _complyctl_ simplifies compliance checks integration in your development and deployment pipelines. An [OSCAL Assessment Plan][7] can be created and customized once and reused across multiple systems. Ultimately compliance checks can be implemented faster and compliance gaps are caught earlier. This prevents non-compliant configurations from reaching production environments.
  4. **Extensibility with Plugins (including OpenSCAP):** The plugin-based architecture of _complyctl_ makes it incredibly versatile. An example is the _complyctl-openscap-plugin_ , which extends _complyctl’s_ capabilities to use OpenSCAP Scanner and the rich content provided by [scap-security-guide][8] package. This allows an immediate and smooth adoption of _complyctl_ using a well-established assessment engine while providing a modern, OSCAL-driven workflow for managing and executing security compliance checks. It also allows a smooth and gradual transition to other scanner technologies.



By embracing _complyctl_ , Fedora users can more easily maintain a strong security posture.

### Getting Started with complyctl: A Practical Tutorial

Ready to put _complyctl_ to work? It is likely simpler than you expect. The following is a step-by-step guide to start using _complyctl_ on your Fedora system.

#### 1\. Installation

First, install _complyctl_ , if necessary. It is [available as an RPM package][9] in official repositories:

```

    sudo dnf install complyctl

```

#### 2\. Understanding the Workflow

_complyctl_ follows a logical, sequential workflow:

  * **list** : Discover available compliance frameworks.
  * **plan** : Create an OSCAL [Assessment Plan][10] based on a chosen framework. This plan acts as your assessment configuration.
  * **generate** : Generate executable policy artifacts for each installed plugin based on the OSCAL Assessment Plan.
  * **scan** : Call the installed plugins to scan the system using their respective policies and finally aggregate the results in a single OSCAL [Assessment Results][11] file.



Let’s walk through these commands.

#### 3\. Step-by-Step Tutorial

**Step 1: List Available Frameworks**

To begin, you need to know which compliance frameworks _complyctl_ can assess your system against. Currently the _complyctl_ package includes the [CUSP Profile][12] out-of-the-box.

Use the _list_ command to show the available frameworks:

```

    complyctl list

```

This command will output a table, showing the available frameworks. Look for the _Framework ID_ column, as you’ll need this for the next step.

Example:

![][13]

Optionally, you can also include the _–plain_ option for simplified output.

**Step 2: Create an Assessment Plan**

Once you’ve identified a _Framework ID_ , you can create an OSCAL Assessment Plan. This plan defines what will be assessed. The _plan_ command will generate an _assessment-plan.json_ file in the complytime directory.

```

    complyctl plan cusp-fedora

```

This command creates the user workspace in the “complytime” directory:

```

    tree complytime
    complytime/
    └── assessment-plan.json

```

The JSON file is a machine-readable representation of your chosen compliance policy.

**Step 3: Install a plugin**

In this tutorial we will use OpenSCAP Scanner as the underlying technology for compliance checks. So, we also want to install the OpenSCAP plugin for _complyctl_ as well the OpenSCAP content delivered by _scap-security-guide_ package:

```

    sudo dnf install complyctl-openscap-plugin scap-security-guide

```

**Step 4: Generate Policy Artifacts**

With your _assessment-plan.json_ in place, and the desired plugins installed, the _generate_ command translates this declarative plan into policy artifacts for the installed plugins. These are the actual plugin specific instructions _complyctl_ plugins will use to perform the checks.

```

    complyctl generate

```

This command prepares the assessment for execution.

```

    tree complytime/

    complytime/
    ├── assessment-plan.json
    └── openscap
        ├── policy
        │   └── tailoring_policy.xml
        ├── remediations
        │   ├── remediation-blueprint.toml
        │   ├── remediation-playbook.yml
        │   └── remediation-script.sh
        └── results

```

**Step 5: Execute the Compliance Scan**

Finally, the _scan_ command runs the assessment using the installed plugins. The results will appear in the _assessment-results.json_ , file by default.

```

    complyctl scan

```

For human-readable output, which is useful for review and reporting, you can add the _–with-md_ option. This will generate both _assessment-results.json_ and _assessment-results.md_ files.

```

    complyctl scan --with-md

```

This Markdown file provides a clear, digestible summary of your system’s compliance status, making it easy to share with auditors or other stakeholders.

```

    tree complytime/
    complytime/
    ├── assessment-plan.json
    ├── assessment-results.json
    ├── assessment-results.md
    └── openscap
        ├── policy
        │   └── tailoring_policy.xml
        ├── remediations
        │   ├── remediation-blueprint.toml
        │   ├── remediation-playbook.yml
        │   └── remediation-script.sh
        └── results
            ├── arf.xml
            └── results.xml

```

### **Final thoughts**

_complyctl_ is an open-source tool built for and by the community. We encourage you to give it a try.

  * Find us on GitHub at [complyctl repository][5].
  * If you find an issue or have a feature request, please open an issue, propose a PR, or contact the maintainers. Your feedback will help shape the future of this tool.
  * Collaboration on [ComplianceAsCode/content][14] community is also welcome to help us shaping [Compliance profiles][15] for Fedora.



--------------------------------------------------------------------------------

via: https://fedoramagazine.org/effortless-flexible-scalable-and-standardized-compliance-checks-for-fedora-using-complyctl/

作者：[Marcus Burghardt][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/marcusburghardt/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/09/intro_2_complyctl-816x345.jpg
[2]: https://unsplash.com/@babybluecat?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/green-textile-with-white-light-CYqr3bsk_tg?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://github.com/complytime
[5]: https://github.com/complytime/complyctl
[6]: https://pages.nist.gov/OSCAL/
[7]: https://pages.nist.gov/OSCAL/learn/concepts/layer/assessment/
[8]: https://src.fedoraproject.org/rpms/scap-security-guide
[9]: https://src.fedoraproject.org/rpms/complyctl
[10]: https://pages.nist.gov/OSCAL/learn/concepts/layer/assessment/assessment-plan/
[11]: https://pages.nist.gov/OSCAL/learn/concepts/layer/assessment/assessment-results/
[12]: https://github.com/ComplianceAsCode/content/blob/master/controls/cusp_fedora.yml
[13]: https://fedoramagazine.org/wp-content/uploads/2025/09/complyctl_list-1024x299.png
[14]: https://github.com/ComplianceAsCode/content
[15]: https://github.com/ComplianceAsCode/oscal-content/tree/main
