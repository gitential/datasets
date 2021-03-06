# Gitential Datasets for Open Source Projects

`TLDR`: Raw GIT data extracted via [libgit2](https://libgit2.github.com/) for a couple of open source projects.

Each directory contains sample `CSV` files and a `README` with the download links (`Parquet` and `JSON` formats).

Our intention to publish further data (a lot actually) with additional metrics and dimensions.

Please feel free to request datasets for other repositories and/or projects in the issues!


## Schema

### Commits

<table>
  <thead>
    <tr>
      <th>Column</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th align="right">id</th>
      <td>string</td>
      <td>The commit's SHA</td>
    </tr>
    <tr>
      <th align="right">delay</th>
      <td>int64</td>
      <td>Seconds elapsed between the creation and last application of the
  commit (rebases can cause negative values)</td>
    </tr>
    <tr>
      <th align="right">age</th>
      <td>int64</td>
      <td>Shortest interval between the commit and it's parents</td>
    </tr>
    <tr>
      <th align="right">ismerge</th>
      <td>bool</td>
      <td>Whether the commit has two or more parents (or is a squash)</td>
    </tr>
    <tr>
      <th align="right">squashof</th>
      <td>int64</td>
      <td>Whether it is a squash and merge commit (currently parsed from commit message)</td>
    </tr>
    <tr>
      <th align="right">author_name</th>
      <td>string</td>
      <td>The author's name</td>
    </tr>
    <tr>
      <th align="right">author_email</th>
      <td>string</td>
      <td>The author's email address</td>
    </tr>
    <tr>
      <th align="right">committer_name</th>
      <td>string</td>
      <td>The committer's name</td>
    </tr>
    <tr>
      <th align="right">committer_email</th>
      <td>string</td>
      <td>The committer's email address</td>
    </tr>
    <tr>
      <th align="right">author_time</th>
      <td>datetime</td>
      <td>The author signature's timestamp</td>
    </tr>
    <tr>
      <th align="right">committer_time</th>
      <td>datetime</td>
      <td>The committer signature's timestamp</td>
    </tr>
    <tr>
      <th align="right">loc_d</th>
      <td>int64</td>
      <td>Number of lines deleted in this commit</td>
    </tr>
    <tr>
      <th align="right">loc_i</th>
      <td>int64</td>
      <td>Number of lines inserted in this commit</td>
    </tr>
    <tr>
      <th align="right">comp_d</th>
      <td>int64</td>
      <td>Whitespace complexity deleted in this commit</td>
    </tr>
    <tr>
      <th align="right">comp_i</th>
      <td>int64</td>
      <td>Whitespace complexity inserted in this commit</td>
    </tr>
    <tr>
      <th align="right">nfiles</th>
      <td>int64</td>
      <td>Number of files (paches) affected by this commit</td>
    </tr>
    <tr>
      <th align="right">message</th>
      <td>string</td>
      <td>The (nice and shiny and fixless :) commit messages</td>
    </tr>
    <tr>
      <th align="right">ndiffs</th>
      <td>int64</td>
      <td>Number of diffs and parent commits</td>
    </tr>
    <tr>
      <th align="right">author_email_dedup</th>
      <td>string</td>
      <td>Author's deduplicated email address</td>
    </tr>
    <tr>
      <th align="right">author_name_dedup</th>
      <td>string</td>
      <td>Author's deduplicated name</td>
    </tr>
    <tr>
      <th align="right">committer_email_dedup</th>
      <td>string</td>
      <td>Committer's deduplicated email address</td>
    </tr>
    <tr>
      <th align="right">committer_name_dedup</th>
      <td>string</td>
      <td>Committer's deduplicated name</td>
    </tr>
  </tbody>
</table>


### Patches

These are the individual files touched by commits. Patches are generated by
diffing two revisions.

<table>
  <thead>
    <tr>
      <th>Column</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th align="right">id</th>
      <td>string</td>
      <td>The commit the patch belongs to</td>
    </tr>
    <tr>
      <th align="right">parent_id</th>
      <td>string</td>
      <td>The parent commit which the diff was generated against</td>
    </tr>
    <tr>
      <th align="right">oldpath</th>
      <td>string</td>
      <td>The file's old path before applying the patch</td>
    </tr>
    <tr>
      <th align="right">newpath</th>
      <td>string</td>
      <td>The file's new path after applying the patch</td>
    </tr>
    <tr>
      <th align="right">ismerge</th>
      <td>bool</td>
      <td>Whether the commit has two or more parents (or is a squash)</td>
    </tr>
    <tr>
      <th align="right">status</th>
      <td>string</td>
      <td>What kind of modification happened with the file (added / deleted /
  modified / etc)</td>
    </tr>
    <tr>
      <th align="right">author_time</th>
      <td>datetime</td>
      <td>The author signature's timestamp</td>
    </tr>
    <tr>
      <th align="right">oldsize</th>
      <td>int64</td>
      <td>The file's size in bytes before applying the patch</td>
    </tr>
    <tr>
      <th align="right">newsize</th>
      <td>int64</td>
      <td>The file's size in bytes after applying the patch</td>
    </tr>
    <tr>
      <th align="right">language</th>
      <td>string</td>
      <td>Programming language of this patch</td>
    </tr>
    <tr>
      <th align="right">langtype</th>
      <td>string</td>
      <td>Language types given by Github's linguist</td>
    </tr>
    <tr>
      <th align="right">skipped</th>
      <td>string</td>
      <td>Whether the patch generation has been skipped or NOT (otherwise the reason)</td>
    </tr>
    <tr>
      <th align="right">istest</th>
      <td>bool</td>
      <td>Whether the file is a test file or not</td>
    </tr>
    <tr>
      <th align="right">loc_d</th>
      <td>int64</td>
      <td>Number of lines deleted in this patch</td>
    </tr>
    <tr>
      <th align="right">loc_i</th>
      <td>int64</td>
      <td>Number of lines inserted in this patch</td>
    </tr>
    <tr>
      <th align="right">comp_d</th>
      <td>int64</td>
      <td>Whitespace complexity deleted in this commit</td>
    </tr>
    <tr>
      <th align="right">comp_i</th>
      <td>int64</td>
      <td>Whitespace complexity inserted in this commit</td>
    </tr>
    <tr>
      <th align="right">loc_d_std</th>
      <td>float32</td>
      <td>Deleted number of lines deviation in the hunks</td>
    </tr>
    <tr>
      <th align="right">loc_i_std</th>
      <td>float32</td>
      <td>Inserted number of lines deviation in the hunks</td>
    </tr>
    <tr>
      <th align="right">comp_d_std</th>
      <td>float32</td>
      <td>Deleted complexity deviation in the hunks</td>
    </tr>
    <tr>
      <th align="right">comp_i_std</th>
      <td>float32</td>
      <td>Inserted complexity deviation in the hunks</td>
    </tr>
    <tr>
      <th align="right">nhunks</th>
      <td>int64</td>
      <td>Number of hunks in this patch</td>
    </tr>
    <tr>
      <th align="right">nblames</th>
      <td>int64</td>
      <td>Number of unique commits this patch has churned lines from</td>
    </tr>
    <tr>
      <th align="right">blame_loc</th>
      <td>int64</td>
      <td>Number of lines this patches has churned (deleted)</td>
    </tr>
  </tbody>
</table>


### Blames

Contains blame segments for patches, an [example](https://github.com/libgit2/libgit2/blame/master/src/blame.c) from libgit2's github page.

<table>
  <thead>
    <tr>
      <th>Column</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th align="right">id</th>
      <td>string</td>
      <td>The commit's SHA</td>
    </tr>
    <tr>
      <th align="right">author_email</th>
      <td>string</td>
      <td>The author's email address</td>
    </tr>
    <tr>
      <th align="right">author_time</th>
      <td>datetime</td>
      <td>The author signature's timestamp</td>
    </tr>
    <tr>
      <th align="right">ismerge</th>
      <td>bool</td>
      <td>Whether the commit has two or more parents (or is a squash)</td>
    </tr>
    <tr>
      <th align="right">newpath</th>
      <td>string</td>
      <td>The file's new path after applying the patch</td>
    </tr>
    <tr>
      <th align="right">istest</th>
      <td>bool</td>
      <td>Whether the file is a test file or not</td>
    </tr>
    <tr>
      <th align="right">blame_id</th>
      <td>string</td>
      <td>The commit's SHA where this commit has churned lines from</td>
    </tr>
    <tr>
      <th align="right">loc_d</th>
      <td>int64</td>
      <td>Number of churned lines</td>
    </tr>
    <tr>
      <th align="right">language</th>
      <td>string</td>
      <td>Programming language of the affected file</td>
    </tr>
    <tr>
      <th align="right">blame_author_email</th>
      <td>string</td>
      <td>The churned author's email address</td>
    </tr>
    <tr>
      <th align="right">blame_author_time</th>
      <td>datetime</td>
      <td>The author signature's timestamp of the chirned commit</td>
    </tr>
    <tr>
      <th align="right">blame_ismerge</th>
      <td>bool</td>
      <td>Whether the churned commit was a merge commit or not</td>
    </tr>
    <tr>
      <th align="right">author_email_dedup</th>
      <td>string</td>
      <td>Author's deduplicated email address</td>
    </tr>
    <tr>
      <th align="right">author_name_dedup</th>
      <td>string</td>
      <td>Author's deduplicated name</td>
    </tr>
  </tbody>
</table>


### Tags

Both lightweight and annotated tags.

<table>
  <thead>
    <tr>
      <th>Column</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th align="right">id</th>
      <td>string</td>
      <td>The tags's SHA</td>
    </tr>
    <tr>
      <th align="right">name</th>
      <td>string</td>
      <td>The tag's name (in case of annotated)</td>
    </tr>
    <tr>
      <th align="right">message</th>
      <td>string</td>
      <td>The tag's message (in case of annotated)</td>
    </tr>
    <tr>
      <th align="right">type</th>
      <td>int64</td>
      <td>Git object type (mostly commit)</td
    </tr>
    <tr>
      <th align="right">author_time</th>
      <td>datetime</td>
      <td>The timestamp of the tag's creation</td>
    </tr>
  </tbody>
</table>


A more detailed documentation is on the way.


## Python example


### Install Dependencies

Reading Parquet files requires [PyArrow](https://arrow.apache.org/docs/python/install.html)


```bash
conda install -y pandas pyarrow
```

    Fetching package metadata ...............
    Solving package specifications: .

    Package plan for installation in environment /Users/krisz/.pyenv/versions/miniconda3-latest/envs/ml3:

    The following packages will be UPDATED:

        pandas: 0.21.0-py36_0 conda-forge --> 0.22.0-py36_0 conda-forge

    pandas-0.22.0- 100% |################################| Time: 0:00:04   2.30 MB/s


### Download Files

Currently there two formats available: Parquet and JSON


```bash
wget https://s3.amazonaws.com/gitential-com-datasets/libgit2-libgit2/commits.parquet
wget https://s3.amazonaws.com/gitential-com-datasets/libgit2-libgit2/commits.json.gz
```

    --2018-01-15 11:09:00--  https://s3.amazonaws.com/gitential-com-datasets/libgit2-libgit2/commits.parquet
    Resolving s3.amazonaws.com (s3.amazonaws.com)... 52.216.100.149
    Connecting to s3.amazonaws.com (s3.amazonaws.com)|52.216.100.149|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 1483345 (1.4M) [binary/octet-stream]
    Saving to: ‘commits.parquet’

    commits.parquet     100%[===================>]   1.41M   616KB/s    in 2.4s

    2018-01-15 11:09:03 (616 KB/s) - ‘commits.parquet’ saved [1483345/1483345]

    --2018-01-15 11:09:04--  https://s3.amazonaws.com/gitential-com-datasets/libgit2-libgit2/commits.json.gz
    Resolving s3.amazonaws.com (s3.amazonaws.com)... 52.216.100.149
    Connecting to s3.amazonaws.com (s3.amazonaws.com)|52.216.100.149|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 1642853 (1.6M) [application/json]
    Saving to: ‘commits.json.gz’

    commits.json.gz     100%[===================>]   1.57M   903KB/s    in 1.8s

    2018-01-15 11:09:06 (903 KB/s) - ‘commits.json.gz’ saved [1642853/1642853]



### Reading Parquet file


```python
import pandas as pd

commits = pd.read_parquet('./commits.parquet')
```


```python
commits[['id', 'message']].head()
```


<table>
  <thead>
    <tr style="text-align: right;">
      <th>id</th>
      <th>message</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>c15648cbd059b92c177586ab1701a167222c7681</td>
      <td>Initial draft of libgit2\n\nSigned-off-by: Sha...</td>
    </tr>
    <tr>
      <td>44181c23ea6c39d51a4b481dc59ecf2cc3967e76</td>
      <td>Mark git_oid parameters const when they should...</td>
    </tr>
    <tr>
      <td>46d8b885bd65158e8cb53266ba4b627b5991bce8</td>
      <td>Rename git_odb_sread to just git_odb_read\n\nM...</td>
    </tr>
    <tr>
      <td>171aaf21d9f7582270c390962f61d3d2613c4d59</td>
      <td>Hide GIT_{BEGIN,END}_DECL from doxygen as its ...</td>
    </tr>
    <tr>
      <td>b51eb250ed0cbda59d3108d04569fab9413909fd</td>
      <td>Cleanup git_odb documentation formatting\n\nSi...</td>
    </tr>
  </tbody>
</table>


### Reading JSON.gz file


```python
import pandas as pd

commits = pd.read_json('./commits.json.gz', compression='infer')
```


```python
commits[['id', 'message']].head()
```


<table>
  <thead>
    <tr style="text-align: right;">
      <th>id</th>
      <th>message</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>c15648cbd059b92c177586ab1701a167222c7681</td>
      <td>Initial draft of libgit2\n\nSigned-off-by: Sha...</td>
    </tr>
    <tr>
      <td>44181c23ea6c39d51a4b481dc59ecf2cc3967e76</td>
      <td>Mark git_oid parameters const when they should...</td>
    </tr>
    <tr>
      <td>46d8b885bd65158e8cb53266ba4b627b5991bce8</td>
      <td>Rename git_odb_sread to just git_odb_read\n\nM...</td>
    </tr>
    <tr>
      <td>171aaf21d9f7582270c390962f61d3d2613c4d59</td>
      <td>Hide GIT_{BEGIN,END}_DECL from doxygen as its ...</td>
    </tr>
    <tr>
      <td>b51eb250ed0cbda59d3108d04569fab9413909fd</td>
      <td>Cleanup git_odb documentation formatting\n\nSi...</td>
    </tr>
  </tbody>
</table>
