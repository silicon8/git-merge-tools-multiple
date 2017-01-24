# git-merge-tools-multiple
The following [.gitconfig](.gitconfig) file has two mergetools defined: vsDiffMerge.exe (Visual Studio) and WinMerge.exe (Win Merge). Ensure that you update your PATH environment variable to include the location of these executables.

    [diff]
      tool = vsdiffmerge
    [difftool]
      prompt = true
    [difftool "vsdiffmerge"]
      cmd = \"vsDiffMerge.exe\" \"$LOCAL\" \"$REMOTE\" //t
      keepbackup = false
      trustExitCode = true
    [difftool "winmerge"]
      cmd = \"WinMergeU.exe\" -u -e $LOCAL $REMOTE
      trustExitCode = true
    [merge]
      tool = vsdiffmerge
    [mergetool]
      prompt = true
    [mergetool "vsdiffmerge"]
      cmd = \"vsDiffMerge.exe\" \"$LOCAL\" \"$REMOTE\" \"$BASE\" \"$MERGED\" //m
      keepbackup = false
      keepTemporaries = false
      trustExitCode = true
    [mergetool "winmerge"]
      cmd = \"WinMergeU.exe\" -e -ub -x -wl -u -maximise -dl \"$LOCAL\" -dr \"$REMOTE\" $LOCAL $REMOTE $MERGED
      keepbackup = false
      keepTemporaries = false
      trustExitCode = true


### To use the default mergetool
    git mergetool

### To use a specific mergetool
    git mergetool --tool=winmerge
