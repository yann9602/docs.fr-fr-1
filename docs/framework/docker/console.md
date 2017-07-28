---
title: "Exécution d’applications console dans Docker"
description: "Découvrez comment prendre une application console .NET Framework existante et l’exécuter dans un conteneur Docker Windows."
author: spboyer
keywords: .NET, Conteneur, Console, Applications
ms.date: 09/28/2016
ms.topic: article
ms.prod: .net-framework
ms.technology: vs-ide-deployment
ms.devlang: dotnet
ms.assetid: 85cca1d5-c9a4-4eb2-93e6-4f878de07fd7
ms.translationtype: Human Translation
ms.sourcegitcommit: 890c058bd09893c2adb185e1d8107246eef2e20a
ms.openlocfilehash: 4f1034763e4dae3711694b441b7a64b40cc99456
ms.contentlocale: fr-fr
ms.lasthandoff: 04/18/2017

---

# <a name="running-console-applications-in-windows-containers"></a>Exécution d’applications console dans des conteneurs Windows

Les applications console sont utilisées à de nombreuses fins, allant de la simple interrogation d’un état à l’exécution de longues tâches de traitement d’images de document. Dans tous les cas, vous pouvez démarrer et faire évoluer ces applications dans les limites des acquisitions matérielles, des temps de démarrage et de l’exécution de plusieurs instances.

En déplaçant vos applications console pour utiliser des conteneurs Windows Server et Docker, vous pouvez les démarrer à partir d’un état propre, leur permettant d’effectuer l’opération, puis de s’arrêter proprement. Cette rubrique décrit les étapes nécessaires pour déplacer une application console vers un conteneur Windows et la démarrer à l’aide d’un script PowerShell.

L’exemple d’application console est un exemple simple qui prend un argument, en l’occurrence une question, et retourne une réponse aléatoire. Cette opération pourrait traiter les taxes d’un client à partir de son `customer_id` ou créer une miniature pour un argument `image_url`.

`Environment.MachineName` a été ajouté à la réponse pour afficher la différence entre l’exécution de l’application localement et son exécution dans un conteneur Windows. Selon que vous exécutez l’application localement ou dans un conteneur Windows, c’est le nom de votre ordinateur local ou l’ID de session du conteneur qui est retourné.

L’exemple complet est disponible dans le [dépôt dotnet / docs sur GitHub](https://github.com/dotnet/docs/tree/master/samples/framework/docker/ConsoleRandomAnswerGenerator). Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Vous devez être familiarisé avec certains termes Docker avant de procéder au déplacement de votre application vers un conteneur.

> Une *image Docker* est un modèle en lecture seule qui définit l’environnement pour un conteneur en cours d’exécution, notamment le système d’exploitation (SE), les composants système et l’application (ou les applications).

Une fonctionnalité importante des images Docker est qu’elles sont composées à partir d’une image de base. Chaque nouvelle image ajoute un petit ensemble de fonctionnalités à une image existante. 

> Un *conteneur Docker* est une instance en cours d’exécution d’une image. 

Vous faites évoluer une application en exécutant la même image dans plusieurs conteneurs.
Conceptuellement, cette opération est similaire à l’exécution de la même application dans plusieurs hôtes.

Vous pouvez en savoir plus sur l’architecture de Docker en consultant [Docker Overview](https://docs.docker.com/engine/understanding-docker/) (Vue d’ensemble de Docker) sur le site Docker. 

Le déplacement de votre application console se fait en quelques étapes.

1. [Générer l’application](#building-the-application)
1. [Création d’un fichier Dockerfile pour l’image](#creating-the-dockerfile)
1. [Processus pour générer et exécuter le conteneur Docker](#creating-the-image)

## <a name="prerequisites"></a>Prérequis
Les conteneurs Windows sont pris en charge sur [Mise à jour anniversaire Windows 10](https://www.microsoft.com/en-us/software-download/windows10/) ou [Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server).

> [!NOTE]
>Si vous utilisez Windows Server 2016, vous devez activer manuellement les conteneurs dans la mesure où le programme d’installation de Docker pour Windows n’active pas cette fonctionnalité. Vérifiez que toutes les mises à jour ont été exécutées pour le système d’exploitation, puis suivez les instructions indiquées dans l’article [Déploiement d’un hôte de conteneurs](https://msdn.microsoft.com/virtualization/windowscontainers/deployment/deployment) pour installer les fonctionnalités Docker et les conteneurs.

Vous devez disposer de Docker pour Windows, version 1.12 bêta 26 ou ultérieure, pour prendre en charge les conteneurs Windows. Par défaut, Docker autorise les conteneurs Linux ; basculez vers les conteneurs Windows en cliquant avec le bouton droit sur l’icône Docker dans la barre d’état système et en sélectionnant **Switch to Windows containers** (Basculer vers les conteneurs Windows). Docker exécute le processus de modification et un redémarrage peut être nécessaire.

![Conteneurs Windows](./media/console/SwitchContainer.png)

## <a name="building-the-application"></a>Génération de l’application
En général, les applications console sont distribuées par le biais d’un programme d’installation, de FTP ou d’un déploiement avec partage de fichiers. Pendant le déploiement sur un conteneur, les ressources doivent être compilées et transférées vers un emplacement qui peut être utilisé au moment de la création de l’image Docker.

Dans *build.ps1*, le script utilise [MSBuild](https://msdn.microsoft.com/library/dd393574.aspx) pour compiler l’application afin de terminer la tâche de création des ressources. Quelques paramètres sont passés à MSBuild pour finaliser les ressources nécessaires : le nom de la solution ou du fichier de projet à compiler, l’emplacement de la sortie et enfin la configuration (débogage ou release).

Dans l’appel à `Invoke-MSBuild`, `OutputPath` est défini sur **publish** et `Configuration` sur **Release**. 

```
function Invoke-MSBuild ([string]$MSBuildPath, [string]$MSBuildParameters) {
    Invoke-Expression "$MSBuildPath $MSBuildParameters"
}

Invoke-MSBuild -MSBuildPath "MSBuild.exe" -MSBuildParameters ".\ConsoleRandomAnswerGenerator.csproj /p:OutputPath=.\publish /p:Configuration=Release"
```

## <a name="creating-the-dockerfile"></a>Création du fichier Dockerfile
L’image de base utilisée pour une application console .NET Framework est `microsoft/windowsservercore`, disponible publiquement sur le [Hub Docker](https://hub.docker.com/r/microsoft/windowsservercore/). L’image de base contient une installation minimale de Windows Server 2016, .NET Framework 4.6.2, et sert d’image de système d’exploitation de base pour les conteneurs Windows.

```
FROM microsoft/windowsservercore
ADD publish/ /
ENTRYPOINT ConsoleRandomAnswerGenerator.exe
```
La première ligne du fichier Dockerfile désigne l’image de base à l’aide de l’instruction [`FROM`](https://docs.docker.com/engine/reference/builder/#/from). Ensuite, l’instruction [`ADD`](https://docs.docker.com/engine/reference/builder/#/add) dans le fichier copie les ressources de l’application à partir du dossier **publish** vers le dossier racine du conteneur. Enfin, le paramètre [`ENTRYPOINT`](https://docs.docker.com/engine/reference/builder/#/entrypoint) de l’image indique qu’il s’agit de la commande ou de l’application qui s’exécute au démarrage du conteneur. 

## <a name="creating-the-image"></a>Création de l’image
Pour créer l’image Docker, le code suivant est ajouté au script *build.ps1*. Quand le script est exécuté, l’image `console-random-answer-generator` est créée en utilisant les ressources compilées à partir de MSBuild, comme défini dans la section [Génération de l’application](#building-the-application).

```powershell
$ImageName="console-random-answer-generator"

function Invoke-Docker-Build ([string]$ImageName, [string]$ImagePath, [string]$DockerBuildArgs = "") {
    echo "docker build -t $ImageName $ImagePath $DockerBuildArgs"
    Invoke-Expression "docker build -t $ImageName $ImagePath $DockerBuildArgs"
}

Invoke-Docker-Build -ImageName $ImageName -ImagePath "."
```

Exécutez le script à l’aide de `.\build.ps1` à partir de l’invite de commandes PowerShell.

Quand la build est terminée, vous pouvez utiliser la commande `docker images` à partir d’une ligne de commande ou d’une invite de commandes PowerShell pour constater que l’image est créée et prête à être exécutée.

```
REPOSITORY                        TAG                 IMAGE ID            CREATED             SIZE
console-random-answer-generator   latest              8f7c807db1b5        8 seconds ago       7.33 GB
```

## <a name="running-the-container"></a>Exécution du conteneur
Vous pouvez démarrer le conteneur à partir de la ligne de commande en utilisant les commandes Docker.

```
docker run console-random-answer-generator "Are you a square container?"
```

La sortie est la suivante :

```
The answer to your question: 'Are you a square container?' is Concentrate and ask again on (70C3D48F4343)
```

Si vous exécutez la commande `docker ps -a` à partir de PowerShell, vous pouvez voir que le conteneur existe toujours.

```
CONTAINER ID        IMAGE                             COMMAND                  CREATED             STATUS                          
70c3d48f4343        console-random-answer-generator   "cmd /S /C ConsoleRan"   2 minutes ago       Exited (0) About a minute ago      
```

La colonne STATUS indique que l’application s’est terminée et qu’elle a pu être arrêtée environ une minute auparavant (« About a minute ago »). Si la commande était exécutée une centaine de fois, une centaine de conteneurs demeureraient statiques sans aucune tâche à effectuer. Dans le scénario initial, l’opération idéale était d’effectuer le travail, puis de procéder à un arrêt ou nettoyage. Pour accomplir ce flux de travail, l’ajout de l’option `--rm` à la commande `docker run` permet de supprimer le conteneur dès la réception du signal `Exited`.

```
docker run --rm console-random-answer-generator "Are you a square container?"
```

Exécutez la commande avec cette option, puis consultez le résultat de la commande `docker ps -a` ; vous pouvez constater que l’ID de conteneur (`Environment.MachineName`) n’est pas dans la liste.

### <a name="running-the-container-using-powershell"></a>Exécution du conteneur à l’aide de PowerShell
Les exemples de fichiers de projet contiennent également un script *run.ps1* qui montre comment utiliser PowerShell pour exécuter l’application acceptant les arguments.

Pour ce faire, ouvrez PowerShell et utilisez la commande suivante :

```
.\run.ps1 "Is this easy or what?"
```

## <a name="summary"></a>Résumé
Simplement en ajoutant un fichier Dockerfile et en publiant l’application, vous pouvez exécuter vos applications console .NET Framework dans des conteneurs et tirer enfin parti de l’exécution de plusieurs instances, d’un démarrage/arrêt propre et d’autres fonctionnalités de Windows Server 2016 sans apporter de modification au code de l’application.

