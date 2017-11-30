---
title: "À l’aide de Visual Studio Tools pour Docker (Visual Studio sous Windows)"
description: Cycle de vie Application en conteneur Docker avec la plate-forme Microsoft et les outils
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: d7a24633f5857bc5b72ebab42020627c645f4302
ms.sourcegitcommit: 6f49c973f62855ffd6c4a322903e7dd50c5c1b50
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2017
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a>À l’aide de Visual Studio Tools pour Docker (Visual Studio sous Windows)

Le flux de travail de développement lors de l’utilisation de Visual Studio Tools pour Docker est semblable au workflow lors de l’utilisation de Code Visual Studio et Docker CLI (en fait, il est basé sur le même CLI Docker), mais il est plus facile de commencer, simplifie le processus et fournit une plus grande la productivité lors de la build, exécuter et composer des tâches. Il est également en mesure d’exécuter et déboguer vos conteneurs via des actions simples comme F5 et Ctrl + F5 dans Visual Studio. De plus, avec Visual 2017 Studio, en plus de pouvoir exécuter et déboguer un seul conteneur, vous également pouvez exécuter et déboguer un groupe de conteneurs (une solution dans son intégralité) en même temps si elles sont définies dans le même fichier docker-compose.yml au niveau de la solution.

## <a name="configuring-your-local-environment"></a>Configuration de votre environnement local

Avec les versions plus récentes de Docker pour Windows, il est plus facile que jamais à développer des applications de Docker, car le programme d’installation est simple, comme expliqué dans les références suivantes.

**Plus d’informations :** pour en savoir plus sur l’installation de Docker pour Windows, accédez à <https://docs.docker.com/docker-for-windows/>.

Si vous utilisez Visual Studio 2015, vous devez disposer de mise à jour 3 ou une version ultérieure ainsi que Visual Studio Tools pour Docker.

**Plus d’informations :** pour obtenir des instructions sur l’installation de Visual Studio, accédez à [https://www.visualstudio.com/ \ produits/vs-2015-produit-éditions](https://www.visualstudio.com/products/vs-2015-product-editions).

Pour plus d’informations sur l’installation de Visual Studio Tools pour Docker, accédez à <http://aka.ms/vstoolsfordocker> et <https://docs.microsoft.com/dotnet/articles/core/docker/visual-studio-tools-for-docker>.

Si vous utilisez Visual Studio 2017, prise en charge Docker est déjà inclus.

## <a name="using-docker-tools-in-visual-studio-2015"></a>À l’aide d’outils Docker dans Visual Studio 2015

Visual Studio Tools pour Docker fournit un moyen cohérent de développer et valider localement vos conteneurs Docker pour Linux dans un hôte Linux Docker ou ordinateurs virtuels ou vos conteneurs Windows directement sur Windows.

Si vous utilisez un seul conteneur, la première chose que vous devez commencer consiste à activer la prise en charge Docker dans votre projet .NET Core. Pour ce faire, cliquez sur votre fichier projet, comme indiqué dans la Figure 4-25.

![https://I1.visualstudiogallery.msdn.s-msft.com/0f5b2caa-EA00-41c8-b8a2-058c7da0b3e4/image/file/205468/1/Add-docker-support.png](./media/image31.png)

Figure 4-25 : activation de la prise en charge de Docker pour votre projet Visual Studio

## <a name="using-docker-tools-in-visual-studio-2017"></a>À l’aide d’outils Docker dans Visual Studio 2017

Lorsque vous ajoutez la prise en charge de Docker pour un projet de service dans votre solution (voir Figure 4-26), Visual Studio est ajout pas simplement d’un fichier DockerFile à votre projet, il est également Ajout d’une section de service de votre solution docker-compose.yml fichiers (ou créer les fichiers si elles n’est pas existe). Il s’agit d’un moyen simple de commencer la composition de votre solution multicontainer ; Vous pouvez ensuite ouvrir les fichiers compose.yml de docker et les mettre à jour avec des fonctionnalités supplémentaires.

![](./media/image32.png)

Figure 4-26 : activer la prise en charge de la Solution de Docker dans un projet Visual Studio 2017

Cette action ajoute non seulement le fichier DockerFile à votre projet, il ajoute également les lignes de la configuration requise de code pour un compose.yml de docker globales définies au niveau de la solution.

Vous également pourrez activer la prise en charge de Docker lors de la création d’un projet ASP.NET Core dans Visual Studio 2017, comme indiqué dans la Figure 4-27.

![](./media/image33.png)

Figure 4-27 : activation sur la prise en charge Docker lors de la création d’un projet

Après avoir ajouté la prise en charge Docker à votre solution dans Visual Studio, apparaît également une nouvelle arborescence de nœuds dans l’Explorateur de solutions avec les fichiers ajoutés docker-compose.yml, comme illustré dans la Figure 4-28.

![](./media/image34.PNG)

Figure 4-28 : les fichiers compose.yml de docker s’affichent maintenant dans l’Explorateur de solutions

Vous pouvez déployer un multicontainer docker à l’aide d’un fichier unique docker-compose.yml lorsque vous exécutez-composer ; Toutefois, Visual Studio ajoute un groupe d’éléments, donc vous pouvez remplacer les valeurs en fonction de l’environnement (de développement et de production) et l’exécution du type (release et debug). Cette fonctionnalité est expliquée mieux dans les chapitres.

**Plus d’informations :** pour plus d’informations sur la mise en œuvre des services et l’utilisation de Visual Studio Tools pour Docker, lisez les articles suivants :

Générer, déboguer, mettre à jour et actualiser des applications dans un conteneur Docker local : [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

Déployer un conteneur ASP.NET à un hôte Docker distant : [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)


>[!div class="step-by-step"]
[Précédente] (docker-applications-interne-boucle-workflow.md) [suivant] (set-up-windows-containers-with-powershell.md)
