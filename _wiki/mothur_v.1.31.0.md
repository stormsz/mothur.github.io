---
title: 'mothur v.1.31.0'
redirect_from: '/wiki/Mothur_v.1.31.0.html'
---
We are very happy to announce the release of [mothur
v.1.31.0](/wiki/mothur_v.1.31.0) and have a number of exciting new
features to tell you about. First, we have re-implemented the SparCC
program first described by [Friedman and
Alm](https://dx.doi.org/10.1371/journal.pcbi.1002687).
It calculates correlation coefficients that are not sensitive to the
hideous effects of relative abundance data. You can run it with the
[sparcc](/wiki/sparcc) command. Second, we have implemented the
approach described by [Holmes and
colleagues](https://dx.doi.org/10.1371/journal.pone.0030126)
for assigning samples to metacommunities using Dirichlet multinomial
mixture models that we are calling get.metacommunity. Think of it as a
robust way of assigning samples to bins for doing things like finding
enterotypes. Third, through a project carried out with Google's Summer
of Code we have created the
classify.shared command that currently
implements a feature selection algorithm using the random forest
algorithm. It's faster and more accurate than the more commonly used R
packages. Finally, since people are staring to develop their own mock
communities and are interested in using
[shhh.flows](/wiki/shhh.flows) with Ion Torrent data and new 454
platforms, we have created [make.lookup](/wiki/make.lookup) for
making your own lookup file to use with shhh.flows. In our testing, we
don't see much of an effect, but hey, you might. As always, we have a
number of new features that we've added to existing functions. As
always, we've added a number of new options to make your life easier.

Finally, a couple of important announcements. First, Pat will be holding
an R workshop in July and a mothur workshop in August. We assume no
experience for either workshop and you can get more information by
emailing Pat by clicking on the link at the top of this page. Second,
we'd be lying if we told you we didn't keep track of how many times
the original mothur paper has been cited. Watching the number tick up
has been humbling over the past 3 or so years. Well, we're currently
sitting at 983 citations. Thank you, thank you, thank you! We'll be
watching Web of Knowledge to see who gets us to 1000 and will be sending
them a special gift in appreciation. We're honored that we've been
able to help so many people do great research!

## New commands

-   [get.metacommunity](/wiki/get.communitytype) - assign samples
    to metacommunities using the algorithm of [Holmes and
    colleagues](https://dx.doi.org/10.1371/journal.pone.0030126)
-   [sparcc](/wiki/sparcc) - calculate the correlation between OTUs
    using the algorithm of [Friedman and
    Alm](https://dx.doi.org/10.1371/journal.pcbi.1002687)
-   classify.shared - identify features
    (i.e. OTUs) that allow one to distinguish between sets of
    communities using the random forest machine learning algorithm.
-   [make.lookup](/wiki/make.lookup) - create custom lookup files
    for use with [shhh.flows](/wiki/shhh.flows)

## Feature updates

-   [get.sabund](/wiki/get.sabund) &&
    [get.rabund](/wiki/get.rabund) - added count file
-   added intelligent warning in case where a group file is used were a
    design file was needed.
-   [chop.seqs](/wiki/chop.seqs) - added name, group and count
    parameters. If sequences are removed from your fasta file by
    chop.seqs, mothur will create new \*.chop.names, \*.chop.groups and
    \*.chop.count\_table files. -
    [https://forum.mothur.org/viewtopic.php?f=5&t=2136](https://forum.mothur.org/viewtopic.php?f=5&t=2136)
-   [get.oturep](/wiki/get.oturep) - added method parameter.
    Options distance and abundance. Default=distance. -
    [https://forum.mothur.org/viewtopic.php?f=5&t=2131](https://forum.mothur.org/viewtopic.php?f=5&t=2131)
-   [filter.shared](/wiki/filter.shared) - added rarepercent and
    keepties parameters
    (https://forum.mothur.org/viewtopic.php?f=5&t=2007)
-   [unifrac.weighted](/wiki/unifrac.weighted),
    [unifrac.unweighted](/wiki/unifrac.unweighted),
    [parsimony](/wiki/parsimony), [indicator](/wiki/indicator)
    and [phylo.diversity](/wiki/phylo.diversity) - parallelized for
    Windows.
-   [get.lineage](/wiki/get.lineage) and
    [remove.lineage](/wiki/remove.lineage)- added constaxonomy and
    shared parameters
    (https://forum.mothur.org/viewtopic.php?f=3&t=2210)
-   [sens.spec](/wiki/sens.spec) - added square phylip format
-   [create.database](/wiki/create.database) - add count file
-   [pcr.seqs](/wiki/pcr.seqs) - added primer to types oligos can
    read
-   added summary file to current types kept by mothur
-   added modifynames parameter to [set.dir](/wiki/set.dir) -
    [https://forum.mothur.org/viewtopic.php?f=10&t=2324&p=6360#p6360](https://forum.mothur.org/viewtopic.php?f=10&t=2324&p=6360#p6360)

## Bug fixes

-   added OTUlabels to shared file in
    [remove.rare](/wiki/remove.rare) - fixed in 1.30.1
-   windows paralellization of [pairwise.seqs](/wiki/pairwise.seqs)
    cutoff was not passed to thread - fixed in 1.30.1
-   [sffinfo](/wiki/sffinfo) - clipQualRight=0 caused issues with
    rightIndex value in flow file.
-   [pcr.seqs](/wiki/pcr.seqs) - For forward primer trimming with
    aligned sequences and keepdots=t. If the character before the first
    primer base was a base and not a gap the base was not trimmed.
    [https://forum.mothur.org/viewtopic.php?f=4&t=2209](https://forum.mothur.org/viewtopic.php?f=4&t=2209) - fixed
    1.30.2
-   [summary.seqs](/wiki/summary.seqs) - 32bit machines processing
    a file larger than 4G could hang.
-   [pcr.seqs](/wiki/pcr.seqs) - removing primers from aligned
    sequences with keepdots=f could result in an unaligned dataset if
    primers were not found at the same locations. Added gaps to preserve
    alignment.
-   [classify.tree](/wiki/classify.tree) - when name file is given
    everything is unclassified -
    [https://forum.mothur.org/viewtopic.php?f=3&t=2161&p=6116#p6116](https://forum.mothur.org/viewtopic.php?f=3&t=2161&p=6116#p6116)
-   [remove.groups](/wiki/remove.groups)(groups=notValidGroupName,
    \...) mothur removes all of the groups. Fix will ignore invalid
    group and continue.
-   [sff.multiple](/wiki/sff.multiple) - fixed order parameter to
    use A, B and I.
-   [cluster.split](/wiki/cluster.split) - when splitting by
    taxonomy mothur was saving temp fasta files as the "current" fasta
    file.
-   [indicator](/wiki/indicator) - fixed bug with pvalues when
    multiple processors were used.

## Changes to wiki

-   [ homd reference files](https://mothur.s3.us-east-2.amazonaws.com/wiki/homd_reference_files.zip) -
    Version 13

## Registered users

2542
