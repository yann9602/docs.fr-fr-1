---
title: "Déployer des applications .NET existantes en tant que conteneurs Windows"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Déployer des applications .NET existantes en tant que conteneurs Windows"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f9a30605313c06542fabf9689f700ed726445f57
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>Déployer des applications .NET existantes en tant que conteneurs Windows

Déploiements basés sur les conteneurs Windows sont applicables aux optimisée pour le Cloud des applications, les applications cloud en mode natif et DevOps prête pour le Cloud.

Dans ce guide et dans les sections suivantes, nous concentrer sur l’utilisation de conteneurs Windows pour *DevOps prête pour le Cloud* applications, lorsque vous porter des applications de .NET existantes.

## <a name="what-are-containers-linux-or-windows"></a>Présentation des conteneurs (Windows ou Linux)

Les conteneurs sont un moyen d’encapsuler une application dans son propre package isolé. Dans son conteneur, l’application n’est pas affectée par les applications ou les processus qui existent en dehors du conteneur. Tout ce dont l’application varie à exécuter avec succès comme un processus est à l’intérieur du conteneur. Chaque fois que le conteneur peut déplacer, la configuration requise de l’application sera toujours être remplie, en termes de dépendances directes, car il est fourni avec tous les éléments qu’il doit s’exécuter (dépendances de bibliothèque de runtimes et ainsi de suite).

La principale caractéristique d’un conteneur est qu’elle rend l’environnement le même dans des environnements différents, car le conteneur lui-même est fourni avec toutes les dépendances dont il a besoin. Cela signifie que vous pouvez déboguer l’application sur votre ordinateur et ensuite le déployer dans un autre ordinateur, avec le même environnement garanti.

Un conteneur est une instance d’une image de conteneur. Une image de conteneur est un moyen d’empaqueter une application ou un service (par exemple, une capture instantanée), puis le déployer de manière fiable et reproductible. Vous pouvez dire que Docker n’est pas une technologie uniquement-it d’également une philosophie et un processus.

Comme tous les jours, les conteneurs deviennent plus courants, ils deviennent un secteur d’activité à l’échelle de « unité de déploiement ».

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>Avantages des conteneurs (moteur Docker sur Windows ou Linux)

Création d’applications à l’aide de conteneurs et qui peut-être également être défini en tant que blocs de construction léger-offre une augmentation significative de souplesse pour la création, la copie et l’exécution de n’importe quelle application, sur n’importe quelle infrastructure.

Avec des conteneurs, vous pouvez prendre n’importe quelle application de développement en production avec peu ou aucune modification de code, grâce à une intégration Docker sur le cloud, les systèmes d’exploitation et outils de développement Microsoft.

Lorsque vous déployez sur les machines virtuelles ordinaires, vous disposez probablement déjà une méthode en place pour le déploiement d’applications ASP.NET sur vos machines virtuelles. Cependant, il est probable que votre méthode implique plusieurs étapes manuelles ou automatisées des processus complexes à l’aide d’un outil de déploiement comme Puppet ou un outil similaire. Vous devrez peut-être effectuer des tâches telles que la modification des éléments de configuration, copie le contenu de l’application entre les serveurs et l’exécution des programmes le programme d’installation interactif basés sur les installations .msi, suivies de test. Toutes ces étapes dans le déploiement ajoutent des délais et les risques aux déploiements. Vous obtiendrez des erreurs chaque fois qu’une dépendance n’est pas présente dans l’environnement cible.

Dans les conteneurs Windows, le processus d’empaquetage d’applications est entièrement automatisé. Les conteneurs Windows est basée sur la plateforme Docker, qui offre des mises à jour automatiques et les restaurations pour les déploiements de conteneur. La principale amélioration que vous obtenez à partir de l’utilisation du moteur Docker est que vous créez des images, telles que des instantanés de votre application, avec toutes ses dépendances. Les images sont Docker images (images de conteneur Windows, dans ce cas). Les images d’exécuter des applications ASP.NET dans des conteneurs, sans retourner au code source. L’instantané du conteneur devient l’unité de déploiement.

Un grand nombre d’organisations est containerizing applications monolithiques existantes pour les raisons suivantes :

-   **Agilité via l’optimisation du déploiement de la version**. Les conteneurs présentent un contrat d’un déploiement cohérent entre le développement et les opérations. Lorsque vous utilisez des conteneurs, les développeurs ne sont pas entendu dire, « Il fonctionne sur mon ordinateur, pourquoi ne pas en production ? » Ils peuvent simplement le dire, « Il s’exécute sous un conteneur, donc il aurez en production. » L’application empaquetée, avec toutes ses dépendances, peut être exécutée dans n’importe quel environnement conteneur pris en charge. Il s’exécutera la manière qu’il a été conçu pour s’exécuter dans toutes les cibles de déploiement (développement, assurance qualité, de mise en lots, production). Conteneurs éliminer la plupart des frictions lorsqu’ils passent d’une étape à l’autre, ce qui améliore considérablement le déploiement, et vous pouvez expédier plus rapidement.

-   **Réduction des coûts**. Conteneurs de contribuer à réduire les coûts, soit par la consolidation et la suppression du matériel existant, ou d’exécuter des applications à une densité plus élevée par unité du matériel.

-   **Portabilité**. Les conteneurs sont portables et modulaire. Conteneurs docker sont pris en charge sur tout système d’exploitation server (Linux et Windows), dans n’importe quel cloud public principaux (Microsoft Azure, Amazon AWS, Google, IBM) et en local et privé ou les environnements de cloud hybride.

-   **Contrôle**. Les conteneurs offrent un environnement flexible et sécurisé qui est contrôlé au niveau du conteneur. Un conteneur peut être sécurisé, isolé et même limité en définissant des stratégies de contrainte d’exécution sur le conteneur. Comme indiqué dans la section sur les conteneurs Windows, les conteneurs Windows Server 2016 et Hyper-V offrent des options de prise en charge d’entreprise supplémentaires.

Des améliorations significatives dans l’agilité, la portabilité et le contrôle finalement conduire les réductions des coûts importants lorsque vous utilisez des conteneurs pour développer et maintenir des applications.

## <a name="what-is-docker"></a>Qu’est-ce que Docker ?

[Docker](https://www.docker.com/) est un [projet open source](https://github.com/docker/docker) qui automatise le déploiement d’applications en tant que conteneurs portables, autonomes qui peuvent s’exécuter dans le nuage ou sur site. Docker est également un [société](https://www.docker.com/) qui promeut et évolue cette technologie. La société fonctionne en collaboration avec le cloud, Linux et les fournisseurs de Windows, notamment Microsoft.

![](./media/image6.png)

> **Figure 4-6.** Docker déploie des conteneurs à toutes les couches du cloud hybride

À une personne familiarisé avec les machines virtuelles, les conteneurs peuvent sembler très similaire. Un conteneur exécute un système d’exploitation, a un système de fichiers et sont accessibles via un réseau, tout comme un système d’ordinateur physique ou virtuel. Toutefois, la technologie et les concepts derrière les conteneurs sont très différents des machines virtuelles. À partir du point de vue du développeur, un conteneur doit être traité plus comme un processus unique. En fait, un conteneur possède un point d’entrée unique pour un processus.

Conteneurs docker (par souci de simplicité, *conteneurs*) pouvant être exécutées en mode natif Linux et Windows. Lors de l’exécution régulières conteneurs, les conteneurs Windows peuvent s’exécuter uniquement sur les hôtes de Windows (un serveur hôte ou une machine virtuelle), et les conteneurs Linux peuvent s’exécuter uniquement sur les hôtes Linux. Toutefois, dans les versions récentes de conteneurs Windows Server et Hyper-V, un conteneur Linux également peut s’exécuter en mode natif sur Windows Server à l’aide de la technologie Hyper-V d’isolement qui n’est actuellement disponible uniquement dans les conteneurs Windows Server.

Dans un futur proche, des environnements mixtes qui ont des conteneurs Linux et Windows sera possible et même courantes.

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>Avantages des conteneurs Windows pour vos applications .NET existants

Les avantages de l’utilisation de conteneurs Windows sont essentiellement les mêmes avantages que vous obtenez à partir des conteneurs en général. L’utilisation de conteneurs Windows est sur ce qui améliore considérablement la portabilité, flexibilité et le contrôle.

Lorsque nous parlons des applications .NET existantes, nous entendons principalement les applications traditionnelles qui ont été créées à l’aide de .NET Framework. Par exemple, elles peuvent être des applications web ASP.NET traditionnelles-ils n’utilisent pas .NET Core, qui est plus récente et s’exécute inter-plateformes sur Linux, Windows et MacOS.

La dépendance principale dans le .NET Framework est Windows. Elle contient également des dépendances secondaire, comme IIS et System.Web dans ASP.NET traditionnel.

Une application .NET Framework doit exécuter sur Windows, de la période. Si vous souhaitez mettez en conteneur d’applications .NET Framework existantes et vous ne pouvez pas ou ne souhaitez pas investir dans une migration vers .NET Core ( » si elle fonctionne correctement, ne pas migrer »), le seul choix que vous avez des conteneurs est d’utiliser des conteneurs Windows.

Par conséquent, un des principaux avantages des conteneurs Windows est qu’ils vous offrent un moyen de moderniser vos applications .NET Framework existantes qui sont exécutent sur Windows via CONTENEURISATION des données. Enfin, les conteneurs Windows Obtient les avantages que vous cherchez à l’aide de la souplesse de conteneurs, la portabilité et un meilleur contrôle.

## <a name="choose-an-os-to-target-with-net-based-containers"></a>Choisissez un système d’exploitation à cibler avec. Conteneurs NET

Étant donné la diversité des systèmes d’exploitation pris en charge par Docker, ainsi que les différences entre .NET Framework et .NET Core, vous devez cibler un système d’exploitation spécifique et en fonction de l’infrastructure que vous utilisez des versions spécifiques.

Pour Windows, vous pouvez utiliser Windows Server Core ou Nano Server de Windows. Ces versions de Windows fournissent des caractéristiques différentes (comme IIS par rapport à un serveur web auto-hébergé comme Kestrel) qui peuvent être nécessaires aux applications .NET Framework ou .NET Core.

Pour Linux, plusieurs versions sont disponibles et pris en charge dans les images Docker de .NET officiels (par exemple, Debian).

Figure 4-7 indique les versions du système d’exploitation que vous pouvez cibler, selon la version de l’application du .NET Framework.

![](./media/image7.png)

> **Figure 4-7.** Systèmes d’exploitation à la cible en fonction de la version du .NET Framework

Dans les scénarios de migration pour les applications existantes ou héritées qui reposent sur des applications .NET Framework, les dépendances principales sont sur Windows et IIS. La seule option consiste à utiliser des images de Docker basées sur Windows Server Core et le .NET Framework.

Lorsque vous ajoutez le nom de l’image à votre fichier Dockerfile, vous pouvez sélectionner le système d’exploitation et la version à l’aide d’une balise, comme dans les exemples suivants pour les images de conteneur Windows basé sur le .NET Framework :

> | **Tag** | **Version du système et** |
> |---|---|
> | **microsoft/dotnet-framework:4.x-windowsservercore** | .NET framework 4.x sur Windows Server Core |
> | **microsoft/aspnet:4.x-windowsservercore** | .NET framework 4.x avec une personnalisation supplémentaire ASP.NET, sur Windows Server Core |

Pour .NET Core (multiplateforme pour Linux et Windows), les balises ressemble à ceci :

> | **Tag** | **Version du système et**
> |---|---|
> | **microsoft/dotnet:2.0.0-runtime** | .NET core 2.0 runtime uniquement sur Linux |
> | **microsoft/dotnet:2.0.0-runtime-nanoserver** | .NET core 2.0 runtime uniquement sur Windows Nano Server |

### <a name="multi-arch-images"></a>Images arch multiples

À compter de mid 2017, vous pouvez également utiliser une nouvelle fonctionnalité dans Docker appelé [arch multi](https://github.com/moby/moby/issues/15866) images. .NET core Docker images peuvent utiliser arch plusieurs balises. Votre fichier Dockerfile des fichiers n’est plus nécessaire de définir le système d’exploitation que vous ciblez. La fonctionnalité multi-ARCHE permet une balise unique être utilisé dans plusieurs configurations d’ordinateur. Par exemple, avec arch multiples, vous pouvez utiliser une étiquette commune : **microsoft/dotnet:2.0.0-runtime**. Si vous extrayez cette balise à partir d’un environnement de conteneur de Linux, vous obtenez l’image de Debian. Si vous extrayez cette balise à partir d’un environnement de conteneur Windows, vous obtenez l’image Nano Server.

Pour les images de .NET Framework, traditionnel .NET Framework prend en charge uniquement Windows, vous ne pouvez pas utiliser la fonctionnalité ARCHE multiples.

## <a name="windows-container-types"></a>Types de conteneurs Windows

Comme les conteneurs Linux, conteneurs Windows Server sont gérés à l’aide du moteur Docker. Contrairement aux conteneurs de Linux, les conteneurs Windows incluent deux types de conteneurs différents, ou exécutent des conteneurs fois-Windows Server et le niveau d’isolement d’Hyper-V.

**Conteneurs Windows Server**: fournit l’isolation des applications via une technologie d’isolation des processus et l’espace de noms. Un conteneur Windows Server partage un noyau avec l’hôte de conteneur et tous les conteneurs qui sont en cours d’exécution sur l’ordinateur hôte. Ces conteneurs ne fournissent pas une limite de sécurité hostile et ne doivent pas servir à isoler le code non fiable. En raison de l’espace de noyau partagé, ces conteneurs nécessitent la même version de noyau et de la configuration.

**Niveau d’isolement d’Hyper-V**: développe l’isolation fournie par les conteneurs Windows Server en exécutant chaque conteneur sur une machine virtuelle hautement optimisée. Dans cette configuration, le noyau de l’hôte de conteneur n’est pas partagé avec d’autres conteneurs sur le même hôte. Ces conteneurs sont conçus pour hostile mutualisées d’hébergement, avec les mêmes garanties de sécurité d’une machine virtuelle. Étant donné que ces conteneurs ne partagent le noyau avec l’ordinateur hôte ou d’autres conteneurs sur l’ordinateur hôte, ils peuvent exécuter noyaux avec différentes versions et les configurations (avec les versions prises en charge). Par exemple, tous les conteneurs Windows sur Windows 10 permet d’isolation de Hyper-V utilisent la version du noyau de Windows Server et la configuration.

Exécute un conteneur sous Windows, avec ou sans isolement de Hyper-V est une décision de l’exécution. Vous pouvez choisir de créer le conteneur avec l’isolation de Hyper-V initialement et en cours d’exécution, choisissez pour l’exécuter comme un conteneur Windows Server.

### <a name="additional-resources"></a>Ressources supplémentaires

-   **Documentation sur les conteneurs de Windows**

    [https://docs.microsoft.com/virtualization/windowscontainers/](https://docs.microsoft.com/virtualization/windowscontainers/)

-   **Principes de base des conteneurs Windows**

    [https://docs.microsoft.com/virtualization/windowscontainers/about/](https://docs.microsoft.com/virtualization/windowscontainers/about/)

-   **Graphisme d’information : Microsoft et les conteneurs**

    [https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf](https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf)

>[!div class="step-by-step"]
[Précédent](how-to-deploy-existing-net-apps-to-azure-app-service.md)
[Suivant](when-not-to-deploy-to-windows-containers.md)
