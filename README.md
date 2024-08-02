# action-makeobj
Run makeobj to create a simutrans pak file.

makeobjを実行しsimutrans pakファイルを作成します。

## Action Inputs
| Input name | Description | Required | Default |
|:-----------|:------------|:---------|:--------|
| work-directory | Directory to execute makeobj<br>makeobjを実行するディレクトリを指定します | false | "" |
| tilesize | Specify tile size (128, etc.)<br>タイルサイズを指定します(128 など) | false | "" |
| dat-path | Specify dat path<br>datファイルのパスを指定します | false | "" |
| pak-path | Specify pak path<br>pakファイルのパスを指定します | false | "output.pak" |

## Example
This example generates a pak file when a tag is pushed

タグがプッシュされた際にpakを生成する例です。
```yaml
name: Releases

on: 
  push:
    tags:
    - '*'

jobs:
  build:
    runs-on: ubuntu-latest
    permissions:
      contents: write

  - name: Checkout
      uses: actions/checkout@v3

  - name: Create pak
      uses: G-alumi/makeobj-action@v1
      with: 
      work-directory: src
      tilesize: 128
    pak-path: ../vehicle.testcar.pak
```

## note
- work-directory is the directory to be specified with the cd command before executing makeobj.<br>
work-directoryはmakeobjを実行する前にcdコマンドで指定するディレクトリです。

- dat-path pak-path, etc. are arguments passed to the makeobj command.
If not specified, the behavior follows makeobj.<br>
dat-path pak-path などはmakeobjコマンドに渡される引数です。
指定しない場合の挙動はmakeobjに準じます。