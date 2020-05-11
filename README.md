# test-github-via-command-line 

事前にGitHubにtest-github-via-command-lineリポジトリを作成し（README.mdなどは作成しない）下記コマンドを実行

.setup-solution.cmd
```
dotnet new sln

md src
md test
md docs

dotnet new classlib -o ./src/Sample.Core
dotnet new xunit -o ./test/Sample.Test
dotnet sln add --in-root ./src/Sample.Core/Sample.Core.csproj
dotnet sln add --in-root ./test/Sample.Test/Sample.Test.csproj
dotnet add ./test/Sample.Test reference ./src/Sample.Core/Sample.Core.csproj

dotnet new gitignore
echo # Custom setup command >> .gitignore
echo .setup-solution.cmd >> .gitignore

echo # test-github-via-command-line >> README.md

git init
git add *
git commit -m "Initialize"
git remote add origin https://github.com/KurozumiGH/test-github-via-command-line.git
git push -u origin master

```
