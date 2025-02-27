---
title: Compare files using Team Foundation Version Control
titleSuffix: Azure Repos
description: Learn how to compare files using Team Foundation Version Control. You can compare server folders and local folders and view the differences.
ms.assetid: d16677af-ab40-4e8c-99d3-ae54675dcfb6
ms.technology: devops-code-tfvc
ms.topic: how-to
ms.date: 06/30/2022
ms.custom: kr2b-contr-experiment
monikerRange: '<= azure-devops'
---

# Compare files using Team Foundation Version Control

[!INCLUDE [version-lt-eq-azure-devops](../../includes/version-lt-eq-azure-devops.md)]
[!INCLUDE [version-vs-gt-2013](../../includes/version-vs-gt-2013.md)]

This article provides a guide for comparing files when using Team Foundation Version Control (TFVC). If you're using Git for version control, see [Compare files](../../repos/git/review-history.md#compare-files).  

You can compare server folders and local folders to each other, and view the differences between the contents of each folder. You can compare two server files, two local files, or a server file against a local file and view the differences between the files.

> [!NOTE]
> Even if you're not using version control, you can use the Diff window in Visual Studio to compare two files. To open the Diff window directly in Visual Studio, you can use the [devenv.exe tool with the /diff option](/visualstudio/ide/reference/diff) from the Developer Command Prompt to compare any two files on your computer.

## Compare any two files using the Compare dialog box

You can compare any two files using the Compare dialog box. The files can both reside on the local system, both on your Team Foundation Server, or one on each.

1. On the menu bar, choose **View** > **Other Windows** > **Source Control Explorer**.

2. In **Source Control Explorer**, right-click a file and select **Compare**.

   The Compare dialog box appears.

3. Specify the two files you want to compare: one under **Source Path** and the other under **Target Path**:

   - Type a path, or open the **Browse** menu, choose **Local Path** or **Server Path**, and then browse to choose the file.
   - Choose an option from the **Type** menu: **Changeset**, **Date**, **Label**, **Latest Version**, or **Workspace Version**.

     > [!TIP]
     > To compare any two local files, select **Local Path** from both **Browse** dropdown menus in the Compare dialog box.

4. Select **OK**.

## Compare files in your workspace with the most recent version

Compare your work with the latest version on your Team Foundation Server while continuing to make changes.

1. If you aren't already connected to the project that you want to work in, then [connect to the project](../../organizations/projects/connect-to-projects.md).

2. From **Team Explorer**, open the **Pending Changes** view.

3. On the **Pending Changes** view, locate the file in the **Included Changes** list. Select the file and right-click to view the context menu, and then:

   - Select **Compare with Workspace Version** to see what changes you have made to the version you checked out.

     > [!TIP]
     >  You can also press **Shift** and then double-click the file.

   - Select **Compare with Latest Version** to see how the changes you have made compare to the latest version of the file on your Team Foundation Server.

4. The Diff window appears. You can continue to make changes to the file in this window.

   > [!TIP]
   >  You can also use Solution Explorer and Source Control Explorer to compare the file in your workspace with a version of the file on the server. Select a file, right-click to open its context menu, and then select **Compare**. When the Compare dialog box appears, select **OK**.

## Compare two versions of a file in your TFVC history

Compare two versions of a file already checked into Team Foundation Version Control:

1. On the menu bar, select **View** > **Other Windows** > **Source Control Explorer**.

2. In **Source Control Explorer**, right-click a file and select **View History**.

3. Select two versions of the file, right-click and select **Compare**.

## Use the Diff window

When you compare files using the instructions in the previous sections, Visual Studio displays the files in the Diff window. The Diff window shows the difference between two files. If one of the files is checked out in your workspace, you can modify the file as you run the comparison.

> [!NOTE]
> Even if you're not using version control, you can use the Diff window in Visual Studio to compare two files. To open the Diff window directly in Visual Studio, you can use the [devenv.exe tool with the /diff option](/visualstudio/ide/reference/diff) from the Developer Command Prompt to compare any two files on your computer.

![Screenshot shows a comparison of two versions of a file.](media/compare-files/IC558594.png)

![Screenshot shows the comparison window layouts.](media/compare-files/IC556152.png)

![Step 1](media/compare-files/IC756627.png) Deleted text

![Step 2](media/compare-files/IC646325.png) Added text

![Step 3](media/compare-files/IC646326.png) Changed text

![Step 4](media/compare-files/IC646327.png) Code review comment

![Step 5](media/compare-files/IC646328.png) Visual summary of the differences between the files

Here are some tips for working with the Diff window:

- Although **Side-by-side mode** is more effective in most cases, you can use whichever mode works best for you and the code you're examining.

- To skip:

  - To the next difference, choose **Next difference** :::image type="icon" source="media/compare-files/IC558315.gif"::: (Keyboard: **F8**).

  - To the previous difference, choose **Previous difference** :::image type="icon" source="media/compare-files/IC558316.gif"::: (Keyboard: **Shift**+**F8**).

  - Back and forth in the file, choose a section of the ![Step 5](media/compare-files/IC646328.png) visual summary.

- When you participate in a [code review](day-life-alm-developer-suspend-work-fix-bug-conduct-code-review.md), you use the **Diff** window to see the code changes that are the subject of the review. For more information, see [Suspend work, fix a bug, and conduct a code review](day-life-alm-developer-suspend-work-fix-bug-conduct-code-review.md).

## Merge changes between versions

Copy and paste changes from the diff view into the version in your workspace to make quick updates to bring in updates from one version to another.
Merge more complex changes between two versions when you [resolve merge conflicts in TFVC](resolve-team-foundation-version-control-conflicts.md) before you check in changes.

If you need to merge two files with significant differences outside of TFVC conflict resolution, use the [vsdiffmerge command line tool](https://roadtoalm.com/2013/10/22/use-visual-studio-as-your-diff-and-merging-tool-for-local-files).
The `vsdiffmerge` tool allows you to merge changes side-by-side and pick which contents you want to keep for each difference between the files.
Run the command with four file parameters followed by the `/m` flag from the Visual Studio Developer Command Prompt to bring up the merge tool directly against any two files.

The basic syntax for `vsdiffmerge.exe` is:

```cmd
vsdiffmerge.exe "File1" "File2" "Base file" "Result file" /m
```

*File1* and *File2* are the full path to the files you want to merge.
The *Base file* is the full path to the file both files are based off of, and *Result file* is the full path to where you want to write the merged results.

## Next steps

- [Compare folders](compare-folders.md)
- [Difference command](difference-command.md) 
