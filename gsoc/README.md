# GSoC with `aeon`

This page provides information for participating in the Google Summer of Code (GSoC)
2026 program with the `aeon` project. Please read carefully, as failure to follow
instructions may result in your application being rejected.

Take a look at our [list of ideas for 2026 projects](https://github.com/aeon-toolkit/aeon-admin/blob/main/gsoc/gsoc-2026-projects.md).

Thank you for your interest in contributing to `aeon` as part of the GSoC program 
and we look forward to your application!

## GSoC resources

Please read through the following resources before starting:

- [Google's GSoC contributor guide](https://google.github.io/gsocguides/student/)
- [The GSoC FAQ](https://developers.google.com/open-source/gsoc/faq)
- [NumFOCUS's GSoC contributing guide](https://github.com/numfocus/gsoc/blob/master/CONTRIBUTING-students.md)
- [`aeon`'s contributor guide](https://www.aeon-toolkit.org/en/latest/contributing.html)

It is expected that you will follow these guidelines when making your GSoC application
and contributing to `aeon`. The instructions and rules on this page take precedence over
the general GSoC and NumFOCUS guidelines.

## Experience Requirements

Experience requirements will vary by project, and are listed in the project ideas.
We categorise projects by complexity as either Low, Medium, or High and will
expect an increasing amount of background knowledge accordingly. All projects
will require a good understanding of Python programming and Git.

- High-complexity projects are suitable for students/open-source beginners
with a strong background in the project topic:
  - For machine learning projects (i.e. developing estimators or ML framework), a 
  strong background in machine learning/data mining and an understanding of time series 
  as a data structure is required. It is expected that the applicant has completed a 
  course in machine learning at their institution or has equivalent experience. 
  Knowledge of how to properly evaluate machine learning models is expected.
  - If a high-complexity project does not involve machine learning, it is likely that we 
  expect the applicant will bring knowledge and experience with them regarding the 
  topic. Most mentors are machine learning experts and researchers rather than software
  engineers, and we will be looking to develop the project in a way that pushes the
  boundaries.
- Medium-complexity projects are suitable for applicants with some experience in the 
project topic, or open-source contributors with a good understanding of Python and 
Git. These projects may require some knowledge of machine learning or time series 
analysis or the ability to learn more about the topics prior to coding, but not to the
level of high-complexity projects. Applicants should be able to demonstrate their 
understanding of the topic and how it relates to the project.
- Low-complexity projects are suitable for most applicants. These will not 
require extensive knowledge of machine learning or time series analysis, and any 
requirements should be at the level beginners can pick up. Knowledge of 
basic Python programming skills and Git are likely still required.

## Rules

Please follow these rules when making your application and contributions to `aeon`. 
Failure to do so will likely leave a poor impression on mentors and may result in your
application being rejected.

- Read and follow the `aeon` [code of conduct](https://github.com/aeon-toolkit/aeon/blob/main/CODE_OF_CONDUCT.md).
- Ensure you have permission to use another project/person's code (i.e. through a 
licence file) and always attribute the original source if permission is granted 
(i.e. [here](https://github.com/aeon-toolkit/aeon/blob/main/aeon/distances/elastic/_bounding_matrix.py#L63)
and [here](https://github.com/aeon-toolkit/aeon/blob/main/aeon/transformations/collection/convolution_based/_minirocket.py#L55)). 
Even with permission, we may request an alternative implementation.
- We are aware other implementations exist for some of the algorithms requested. Do not 
try to copy and paste this code and pass it off as your own; we have enough experience 
to tell.
- Unless you have talked to the developers/issue creators, please only create pull 
requests for issues with the `GSoC` or `good first issue` label. See the FAQ for more 
details on creating other pull requests.
- Do not abuse AI to create your application or contributions. More information below
and in the contributor guide.
- Do not spam developers with requests to review your pull requests or applications.
- Create your application using the `aeon` GSoC [template](https://github.com/aeon-toolkit/aeon-admin/tree/main/gsoc/application-template.md).

## Use of AI tools

We discourage the use of AI tools in the creation of GSoC applications and as the main 
provider of contributions. Using AI tools to proofread or generate menial code is 
acceptable. We do not care if you are using Copilot to generate a few lines of simple 
code if you understand what you are submitting. If you do use any AI or LLMs in your 
contributions or proposal, please disclose their use in your pull requests and/or write 
up. Additionally, you must fully understand and be able to explain any AI-generated code 
you submit. 

Having AI write your timeline and large chunks of your proposal, or submitting full 
pull requests of noticeably AI-generated content is likely to disqualify your 
application. Undisclosed use of AI/LLMs, or inability to explain AI-generated 
contributions, is likely to have the same result.

## Making an application

Participants will need to submit their proposal(s) to [NumFOCUS on the GSoC webpage](https://summerofcode.withgoogle.com/programs/2025/organizations/numfocus).
The application submission period opens ? and closes ?.

Applicants must use the sections in the `aeon` [template](https://github.com/aeon-toolkit/aeon-admin/tree/main/gsoc/application-template.md) 
to create their application. Note the limit for linking to open-source contributions.
Please follow the following rules when making your application:

- When making your web application please start with `aeon`, followed by a dash and
then the project name i.e. "aeon - My Project". This will help us identify your
application among other NumFOCUS projects. If we cannot find your application, we
will not review it.
- Please use a font size of 10pt or 12pt for standard text, headings can be larger. Use
appropriate line spacing, margins and section structure.
- Applications should be at least 4 pages long, and no longer than 20 pages long
(including figures, tables and references). This is a guideline, do not submit 20
pages of text and expect us to read it all.
- Submit your application as a PDF file.

We also heavily recommend you:

- Make sure your PDF renders correctly and ensure attention to detail. Some errors in
the past include: Broken links, missing sections and typos.
- Include at least one link to a pull request you have made to `aeon` or another
open-source project.

## FAQ

**Q. Where can I talk about GSoC and `aeon` projects?**

Feel free to post and ask questions on our dedicated [GSoC 2026 GitHub discussion](?)
or on our community [Slack](https://join.slack.com/t/aeon-toolkit/shared_invite/zt-36dlmbouu-vajTShUYAHopSXUUVtHGzw).
Use the `#introductions` channel on Slack if you want to introduce yourself to
the community and developers. 

**Q. Can I apply to multiple projects?**

Yes, you can apply to multiple projects. Multiple `aeon` applications need to be 
separate submissions, and each proposal should be distinct and tailored to the project. 
If we feel that you have cut corners making multiple applications and are willing to 
work on any project as long as it is GSoC, we may be less likely to take you on for the 
summer.

If we suspect that you have gone over the three application limit by creating multiple
accounts, we will not accept your application.

**Q. Can you review my pull request?**

We will try and aim to look at all code submissions in a reasonable amount of time. 
This is dependent on the availability of developers during the application period
where traffic is heavy, however. You can add unmerged pull requests to your 
application and pull requests to other open-source projects.

Mentors have dedicated time to mentor accepted applicants during the summer period, so 
do not worry about lack of interaction with project mentors and developers if accepted.

**Q. Can you assign me to issue #XXXX?**

Please read the contributor guide on assigning yourself to issues. For issues without
the `GSoC` and `good first issue` labels, only do so if you are confident you can 
complete it and respond to reviews. If we do not think the pull request is in a 
suitable state, or the time spent to complete it is too high, we may close it.

**Q. Can you review my application before submitting?**

This is unlikely to happen as it is very time-consuming to do this for every applicant. 
A mentor is most likely to accept this request if you have been interacting with the 
community for a while, and you ask very early in the application period.

**Q. I like the idea of project X, can you teach me more about X?**

We are happy to help you understand or clarify our project ideas if you ask mentors.
However, we will not teach you the basics of the topic or any activity which would be
akin to tutoring. Please look at resources for machine learning and time series
before asking questions and applying.

**Q. Project X only mentions algorithm Y, is that all I will need to implement?** 

This is dependent on the project, but we usually won't fully flesh out the projects
in our idea list. This is up to you to do in your application. Applications which
understand related works and make proposals on how to extend the project is there is
additional time will be looked upon more favourably.

**Q. There are a lot of related algorithms that I include my proposal for project X, should I add them all?** 

What you add to your implementation plan is somewhat up to you. Keep in mind that 
a single excellent and well-tested implementation is likely better than three mediocre 
implementations which will be challenging to maintain. Consider the type of project
and the difficulty when creating your plan. Proposing to implement a single algorithm
may give mentors the impression you do not have the experience or confidence to 
implement what they expect. Proposing to implement 15 algorithms may give the impression
you plan to cut corners or copy and paste code from other projects.

**Q. Can I start coding for the project before my application is accepted?**

We have no issue with creating code for the project before projects are announced or 
including code listings in your application. However, it is unlikely we will accept pull 
requests on project topics while applications are open or another applicant is working 
on the project as part of GSoC.

## Acknowledgements

The contents of this page and our templates are based on the [NumFOCUS](https://github.com/numfocus/gsoc) 
and [Internet Health Report](https://github.com/InternetHealthReport/gsoc) GSoC guidance.
