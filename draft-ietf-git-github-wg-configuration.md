---
docname: draft-ietf-git-github-wg-configuration
title: GitHub Configuration for IETF Working Groups
abbrev: WG GitHub Configuration
category: info

ipr: trust200902
area: General
workgroup: GIT Working Group
keyword: Internet-Draft

stand_alone: yes
pi: [toc, sortrefs, symrefs]

author:
 -
    ins: A. Cooper
    name: Alissa Cooper
    organization: Cisco
    email: alcoop@cisco.com

 -
    ins: P. Hoffman
    name: Paul Hoffman
    organization: ICANN
    email: paul.hoffman@icann.org

normative:
  git-protocol:
    title: "Git on the Server - The Protocols"
    target: "https://git-scm.com/book/en/v2/Git-on-the-Server-The-Protocols#The-Git-Protocol"

informative:


--- abstract

The use of GitHub in IETF working group processes is increasing.
This document describes possible uses and conventions for working
groups which are considering starting to use GitHub. It does not
mandate any processes, and does not require changes to the processes
used by current and future working groups not using GitHub.

Discussion of this document takes place on the ietf-and-github mailing list
(ietf-and-github@ietf.org), which is archived at
&lt;https://mailarchive.ietf.org/arch/search?email_list=ietf-and-github&gt;.


--- middle

# Introduction

Many IETF working groups and participants make use of GitHub in different ways as part of
their work on IETF documents. Some others are interested in having their working groups
use GitHub to facilitate the development of working group documents, but they are
unfamiliar with how to get started or they are unclear about which conventions to follow.
Some other working groups use or plan to use other other code
repository services such as GitLab and Bitbucket, which have
different properties than GitHub.


This document proposes a set of administrative processes and conventions for IETF working
groups to use if they chose as a working group to use GitHub to facilitate their work. The
proposals in this document are not directed at working groups or individuals that are
already using GitHub to do IETF work. Practices vary among existing working groups and
some of them are not consistent with the conventions proposed here: that is fine. The goal
of the proposals in this document is not to require uniformity in current practice, but to
help working groups to get started using GitHub in a uniform way if they want to.

The document is meant to spur discussion in the IETF community. If there proves to be
rough consensus in the community in support of the proposals in this document, the
functional requirements would need to be discussed with the IETF Tools Team, and the IETF
Secretariat who would need to support various pieces of what is proposed here.

# Administrative Process and Conventions

This section specifies a proposal for an administrative process and conventions to support
the creation and management of GitHub organizations for working groups and single-document
repositories in a uniform way. The steps could be done manually by the IETF Secretariat or
they could be automated. For example, see
&lt;https://github.com/richsalz/ietf-gh-scripts&gt; and
&lt;https://github.com/martinthomson/i-d-template&gt; for working examples of automation
that is in use in some working groups.

In this document the question of whether processes should be manual or automated is
deliberately left ambiguous since the first question that should be asked is whether this
is functionality the community would want to have supported at all.

Most of the conventions below are drawn from {{?I-D.thomson-github-bcp}}.

## Creation of GitHub Organizations {#creation}

This document proposes that there be a facility in the IETF Datatracker
(&lt;https://datatracker.ietf.org/&gt;) interface to allow an area director or working
group chair to request the creation of a GitHub organization for a particular working
group. Ideally, this facility would appear both as part of the working group chartering UI
as well as the working group page UI.

When an area director or working group chair makes a request to create a GitHub
organization, the following process would be initiated:

1. Create a GitHub organization for the working group.

2. Name the organization as ietf-&lt;wgname&gt;-wg

3. Initialize the organization by designating the IETF Secretariat and the area directors
in the working group's area as owners. If the responsible AD for the working group is from
another area, that AD will be an owner as well.

4. Initialize the organization with a team that has administrator access. This team will
consist of the working group chairs and working group secretary, if one exists.

After the organization is created, the URL for the organization would be added to the
working group's page in the datatracker.

Steps 3 and 4 above imply that the GitHub identities of the organization owners and
administrators are known. Recording GitHub identities in the datatracker (see
&lt;https://trac.tools.ietf.org/tools/ietfdb/ticket/2548&gt;) would facilitate this. The
person requesting the organization would need to be notified if the GitHub identities of
any of the people meant to be owners or administrators were not available.

## Migration of an Existing Organization

If a working group already has an organization, it would be useful to be able
to make it have the same management as one would get with going through the
steps in {{creation}}. That is, it would be good to be able to run steps 3 and
4 from {{creation}} so that the rest of the activities in this section such as
personnel work the same for the organizations that were created on their own.

## Personnel Changes

When there are personnel changes in the area or the working group, those changes would be
reflected in the GitHub organization.
There should likely be an API to specify that there were personnel changes.

## Working Group Closing

When a working group is closed, the team with administrative access would be removed and
the owner list would be returned to its initial composition. The organization summary and
the repositories within the organization would be updated to indicate that they are no
longer under development.

## Creation of Document Repository

There are many different scenarios and configurations where it might be useful to have
automation and/or established administrative conventions for repositories within WG
organizations, such as:

   - Creating a new repository for an individual draft that is at the discretion of the
   WG chair

   - Creating a new repository for an already-adopted working group draft

   - Migrating an existing document repository into the WG organization

   - Creating a new repository that contains multiple drafts

As an incremental step, this document proposes that there be a facility in the Datatracker
interface to allow an administrator of an ietf-&lt;wgname&gt;-wg organization to request
the creation of a new repository within that organization for a single document. The
document authors would be identified as collaborators. The repository name would be the
draft name. Ideally, the repository would be configured with a skeleton draft file,
default CONTRIBUTING, LICENSE, and README files, and continuous integration support, in
the vein of &lt;https://github.com/martinthomson/i-d-template&gt;. 


# Working Group Process

{{?I-D.thomson-github-bcp}} contains discussion of the different possible ways that a
working group can use GitHub and the large number of decisions associated with doing so.
This section proposes a basic set of administrative policies for working groups to follow
and the administrative support needed to carry out those policies.

## Contributions

At a minimum, every repository created in a working group organization needs to
incorporate into its CONTRIBUTING file the boilerplate text at
&lt;https://trustee.ietf.org/license-for-open-source-repositories.html&gt; from the IETF
license file for open source repositories. The CONTRIBUTING file can contain other
information as well (see
&lt;https://github.com/ietf/repo-files/tree/master/contributing-samples&gt; for examples).

It would be useful if the user data in the Datatracker could list (at a minimum) the
GitHub account of the user so that their contributions could be tracked more easily.

## Backing Up and Archiving GitHub Content

IETF working group mailing lists are automatically backed up by the IETF Secretariat, and
the archives are publicly available. All official interactions in a WG must be archived.

It would be good for working group GitHub content to
also be backed up and publicly archived. This document proposes using the git protocol
{{git-protocol}} itself for both of these tasks.

Every IETF working group repository on GitHub will have a mirror repository of the same
name on a server maintained by the IETF Secretariat. Every hour, a service will use the
"git fetch" command on every GitHub repository that is being tracked. The mirror
repository will allow anyone to read the repository.

Note that this system will not back up GitHub issues or pull requests.
These should be backed up as well; the GitHub API allows for this.
The IETF Secretariat should back up those at the same time as it is backing up the GitHub
repositories.

{{?I-D.thomson-github-bcp}} has more discussion of backing up and archiving.

# Security Considerations

An attacker who can change the contents of Internet Drafts, particularly late in a working
group's process, can possibly cause unnoticed changes in protocols that are eventually
adopted.


# IANA Considerations

This document has no IANA actions.

--- back



