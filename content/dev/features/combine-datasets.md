+++
date = "2017-10-19T23:20:47-04:00"
draft = false
title = "Combining Datasets"
description = "Combining datasets lets you track answers to questions repeated across multiple surveys over time."
weight = 20
tags = ["search", "combine datasets"]
categories = ["feature"]
+++

At Crunch, in addition to giving our users tools to process, analyze, and present new data, we are also looking for ways we can help our users to make more use out of older data. The more data you have in Crunch, the more useful it should become. Our new “Combine Datasets” feature unlocks some of the potential of having all the data in one place but that isn’t yet lined up for analysis.

Market researchers will recognize this data structure as that of a **tracking study**. Social scientists will recognize  **time-series cross-sectional data**. Almost all data scientists have faced this kind of ‘stacking’ problem and hacked their way through mystifying idiosyncracies. “Combine Datasets” is a first step as we seek to automate the error-prone and often tedious work of building a tracking study from its component cross-sections.

{{< figure src="../images/CombineDSSearch.png" class="floating-right">}}

This feature allows you to create a new dataset using a subset of variables from multiple datasets, allowing you to track these variables over time. For example, imagine a repeated survey; every month there would be some new and timely questions, new ad campaigns or products included, but many of the same tracking questions might be asked every time – this feature allows you to track the responses to those common questions over all the surveys.

To use this feature, click the + in the bottom left corner while viewing a project and select **Combine Datasets**. The search panel will open, prompting you to search for one key variable of interest. The search results will show how many and which datasets it’s found in to give you a solid foundation for the tracking dataset.

## Selecting Datasets and Variables

Combine Datasets will walk you through selecting which datasets you want to combine and selecting which variables in those datasets you want to be available in your new, combined dataset. This allows you to select multiple, possibly related, variables that are common to multiple datasets, as well as include others like demographics that exist in all or several of the datasets. (Of course, you are free to select a variable that only occurs in one of the series; it’ll just be missing for all the others.)

{{< figure src="../images/CombineDSSelectVar.png" class="centered-image">}}

## Creating Time and Wave variables

{{< figure src="../images/CombineDSSelectOptions.png" class="floating-right">}}
As part of combining datasets, the system can add variables (sometimes called ‘dimensions’) in the combined result that will allow you to track your variables over time (using dataset start dates or end dates) as well as by the source dataset names, which allows you to perform analyses tracking differences over other dimensions, such as region.

## Using the Combined Dataset

When you have finished combining datasets, you’ll be able to open the new dataset, which will contain combined data for all the variables you selected. It will open to a dashboard with the variable you searched for at the beginning and, if you added a wave variable, also show that focal variable over time.

{{< figure src="../images/CombineDSDashboard.png" class="centered-image">}}

## Try it out

Detailed instructions about combining datasets are available at [Combining datasets](http://support.crunch.io/crunch/crunch_combining-datasets.html). Combining datasets is a non-destructive process (the source datasets are not affected), and we encourage you to try it out if you have variables you’d like track over multiple existing datasets. If you do, please let us know what you think and if there are any other capabilities you'd like to see at support@crunch.io.

### What’s Next

We already have big plans to make building tracking studies / combining datasets easier, more flexible, and more automatic — in order to maximize the potential in your data so it doesn’t live in Crunch — it comes alive in Crunch.

Currently, the system makes a number of assumptions about the input data being “clean” in a few ways. To the extent these assumptions limit how useful combine is for your particular data, we view each as an opportunity.

1. Variables are matched by their “alias” across datasets. It may be necessary to use a script to re-alias in the datasets you’re trying to combine. As a best practice, we advise aliases with semantic meaning: “unaided_awareness” is a better alias than “Q1”. We are working on more flexible (some might say magic) matching, though, so the system will be able to line up Q1 and Q21 if we detect that they are actually “the same question”.
2. Variable names and descriptions in the result are taken from the first dataset in the series.
3. The result always has the union of categories, matched exactly by name. Because it’s common to change order  or randomize response categories in different cross-sections, category names are matched and given the ids found in the first dataset of the series. For the moment, spelling, language, and capitalization differences between datasets will result in new categories in the result. Next we plan to let you combine categories by id or code, if you trust that multilingual datasets share consistent ids. Eventually, you’ll be able to edit the detailed category mapping for each constituent dataset.
4. In order to build a useful time or ‘wave’ variable, datasets need to have `start_date`, `end_date`, or both set in their metadata. We know that some datasets have row-level date/time variable, possibly a scalar date, but maybe even a precise collection time. The system will eventually be able to inspect those or use one as the Wave variable. Almost as often datasets encode wave information in their names, notes, or description strings — all of them reasonable approaches.
5. *What if you could go back and edit* any of these parts of the combination “recipe”? That’s where we’re headed.
6. *What if you pointed to a folder* of datasets and said to the system: “figure it out”? One day it will.