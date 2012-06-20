# Nuget 2 & Kudu git publish repro #
This repository exists to repro an exception that occurs when doing 'git push azure master'.

How to reproduce:

- Create new ASP.NET MVC 3 web site (empty)
- Add HomeController with Index action
- Add Index View
- Run to test locally
- Enable nuget package restore
- git init
- git add .
- git remote add azure [your address here]
- git push azure master

Expected: site published

Actual: Fails on error message

> Counting objects: 82, done.
> Delta compression using up to 8 threads.
> Compressing objects: 100% (77/77), done.
> Writing objects: 100% (82/82), 476.24 KiB, done.
> Total 82 (delta 9), reused 0 (delta 0)
> remote: New deployment received.
> remote: Updating branch 'master'.
> remote: Preparing deployment for commit id '9875204017'.
> remote: Building web project 'TestKuduDeployment.csproj'.
> remote: C:\DWASFiles\Sites\kudurepro\VirtualDirectory0\site\repository\.nuget\nuget.targets(76,9): error : Object reference not set to an instance of an object. [C:\DWASFiles\Sites\kudurepro\VirtualDirectory0\site\repository\TestKuduDeployment\TestKuduDeployment.csproj]
> remote: C:\DWASFiles\Sites\kudurepro\VirtualDirectory0\site\repository\.nuget\nuget.target (76,9): error MSB3073: The command ""C:\DWASFiles\Sites\kudurepro\VirtualDirectory0\site\repository\.nuget\nuget.exe" install "C:\DWASFiles\Sites\kudurepro\VirtualDirectory0\site\repository\TestKuduDeployment\packages.config" -source "" -o "C:\DWASFiles\Sites\kudurepro
> \VirtualDirectory0\site\repository\packages"" exited with code 1. [C:\DWASFiles\Sites\kudurepro\VirtualDirectory0\site\repository\TestKuduDeployment\TestKuduDeployment.csproj]
> 