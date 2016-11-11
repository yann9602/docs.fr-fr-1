---
title: Produits .NET
description: Produits .NET
keywords: .NET, .NET Core
author: richlander
manager: wpickett
ms.date: 06/23/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 2e38e9d9-8284-46ee-a15f-199adc4f26f4
translationtype: Human Translation
ms.sourcegitcommit: 15c55a87beb64f265a164db918c7721c7690fadf
ms.openlocfilehash: 90deb1903eea6ae1336326ca91f1e7863485dfd1

---

# <a name="net-products"></a>Produits .NET

.NET est une [spécification](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) très flexible, généraliste, multiplateforme par nature destinée à la génération de produits de développement. Il est utilisé pour toutes les catégories d’application les plus populaires : bureau, mobile, cloud, jeux et IoT.

Deux termes légèrement différents sont utilisés dans ce document :

- « Produit .NET » : permet de générer une application pour une ou plusieurs plateformes cibles.
- « Implémentation .NET » : combinaison d’un runtime, d’un framework et d’outils qui peuvent exécuter du « code.NET » sur lequel reposent les produits.

## <a name="product-categories"></a>Catégories de produits

Les produits .NET sont disponibles pour chacune des catégories de produits suivantes.

### <a name="desktop"></a>Bureau

Vous pouvez générer des applications de bureau pour Windows et macOS.

- [Applications Windows universelles](https://developer.microsoft.com/windows) avec [.NET Native](#net-native)
- [Windows Presentation Foundation (WPF)](https://msdn.microsoft.com/library/ms754130.aspx) pour Windows avec le [.NET Framework](#net-framework)
- [Windows Forms](https://msdn.microsoft.com/library/dd30h2yb.aspx) pour Windows avec le [.NET Framework](#net-framework)
- Cocoa pour macOS avec [Xamarin](#xamarin-sdk)
- [Electron](http://electron.atom.io/) pour bureau multiplateforme avec [electron-edge](https://github.com/kexplo/electron-edge)

### <a name="games"></a>Jeux

Vous pouvez générer des jeux pour de nombreux appareils de bureau, mobiles, consoles et appareils avec réalité augmentée/virtuelle.

- [CRYENGINE](http://docs.cryengine.com/display/CEPROG/CE%23+Programming) avec [Mono](#mono)
- [MonoGame](http://www.monogame.net/documentation/?page=main) avec [Mono](#mono)
- [Unity](http://docs.unity3d.com/Manual/index.html) avec [Mono](#mono)

### <a name="iot"></a>IoT

Vous pouvez générer des applications IoT pour Windows 10 IoT Standard, y compris Raspberry Pi 2/3.

- [Windows 10 IoT Standard](https://developer.microsoft.com/windows/iot) avec [.NET Native](#net-native)

### <a name="mobile"></a>Mobile

Vous pouvez générer des applications mobiles pour iOS, Android et Windows.

- Application iOS avec [Xamarin](#xamarin-sdk)
- Application Android avec [Xamarin](#xamarin-sdk)
- [Application Windows universelle](https://developer.microsoft.com/windows) avec [.NET Native](#net-native)

### <a name="web-and-cloud"></a>Web et cloud

Vous pouvez générer des applications web et cloud pour Windows et Linux.

- [ASP.NET](http://www.asp.net/) pour Windows avec le [.NET Framework](#net-framework)
- [ASP.NET Core](http://docs.asp.net/) pour Windows, macOS et Linux avec [.NET Core](#net-core)

## <a name="net-implementations"></a>Implémentations .NET

Les principales implémentations .NET commerciales et open source sont répertoriées ci-dessous, dans l’ordre alphabétique.

### <a name="net-core"></a>.NET Core

.NET core est utilisé pour générer des applications d’appareil, web, cloud et incorporées/IoT. Il est [open source](https://github.com/dotnet/core) et multiplateforme, prenant en charge Windows, macOS et Linux. [ASP.NET Core](http://docs.asp.net/) est la charge de travail la plus populaire pour .NET Core. Vous pouvez l’utiliser pour générer des services et des applications web, en vue de les déployer localement et sur le cloud. Vous pouvez également utiliser .NET Core pour générer des outils, des utilitaires et des applications de traitement de cloud.

- En savoir plus sur [.NET Core](../core/index.md)
- En savoir plus sur [ASP.NET Core](http://docs.asp.net/)
- [Télécharger .NET Core](http://dot.net/core)

Les principales caractéristiques de .NET Core sont les suivantes :

**Multiplateforme** : .NET Core prend en charge trois familles de systèmes d’exploitation : Linux, Windows et macOS. Les applications .NET Core sont multiplateformes par défaut. Vous pouvez écrire des applications et des bibliothèques qui s’exécutent sans modification sur les systèmes d’exploitation pris en charge.

**Open source** - [.NET Core](https://github.com/dotnet/core) est disponible sur GitHub, sous licences [MIT](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT) et [Apache 2](https://github.com/dotnet/roslyn/blob/master/License.txt) (la gestion des licences est propre à chaque composant). La documentation est concédée sous licence [CC-BY](https://github.com/dotnet/docs/blob/master/license.txt). .NET core utilise également un ensemble significatif de dépendances open source, répertoriées dans les [notes de version .NET Core](https://github.com/dotnet/core/releases). 

**Acquisition naturelle** : .NET Core est distribué sous plusieurs formes, suivant les besoins des développeurs. Vous pouvez acquérir .NET Core avec le programme d’installation [SDK .NET Core](https://dot.net/core) (ou fichiers zip) ou par le biais de gestionnaires de package spécifiques au système d’exploitation, tels qu’APT et Yum. Des [images .NET Core Docker officielles](https://hub.docker.com/r/microsoft/dotnet/) sont disponibles sur le Hub Docker. Des bibliothèques de frameworks plus générales et l’écosystème élargi des bibliothèques .NET sont disponibles sur [NuGet](http://www.nuget.org/). 

**Plateforme modulaire** : .NET Core s’appuie sur une conception modulaire, permettant aux applications d’inclure uniquement les dépendances et bibliothèques .NET Core nécessaires. Chaque application fait ses propres choix en matière de contrôle de version .NET Core, évitant les conflits avec les composants partagés. Cette approche s’aligne sur la tendance qui consiste à développer des logiciels à l’aide de technologies de conteneurs telles que Docker.

### <a name="net-framework"></a>.NET Framework

Le .NET Framework est utilisé pour générer des applications pour Windows et Windows Server. Vous pouvez l’utiliser pour générer des interfaces utilisateur riches avec Windows Presentation Framework (WPF) et Windows Forms. Il prend également en charge la génération d’applications serveur avec ASP.NET Web Forms, ASP.NET MVC et Windows Communication Framework (WCF). Visual Studio fournit des expériences conceptuelles avancées pour le .NET Framework, facilitant la génération d’applications client et serveur. Il est le meilleur choix pour écrire des applications pour Windows.

- En savoir plus sur le [.NET Framework](https://msdn.microsoft.com/library/w0x726c2.aspx)
- [Télécharger le .NET Framework](https://dot.net)

[Windows Forms](https://msdn.microsoft.com/library/dd30h2yb.aspx) vous permet de générer une interface utilisateur de bureau basée sur des formulaires plutôt que sur des données beaucoup plus rapidement que toute autre technologie. Grâce à un concepteur, vous pouvez glisser-déplacer les contrôles d’interface utilisateur et les autres contrôles ; ainsi, la plupart des tâches de développement s’effectuent dans le cadre d’un modèle conceptuel et de mouvements unique.

[Windows Presentation Foundation (WPF)](https://msdn.microsoft.com/library/ms754130.aspx) sépare les problématiques du code et de l’interface utilisateur en décrivant l’interface utilisateur avec le langage de balisage [XAML](https://msdn.microsoft.com/library/ms752059.aspx). WPF est très flexible et est souvent utilisé pour les interfaces utilisateur qui demandent un modèle utilisateur plus complexe ou une apparence plus sophistiquée.

[Windows Communication Foundation (WCF)](https://msdn.microsoft.com/library/ms731082.aspx) est un ensemble de bibliothèques pour les services web SOAP. Il vous permet de créer des services qui peuvent communiquer par le biais de divers protocoles pris en charge utilisant divers formats de données et qui peuvent être hébergés dans le processus de votre choix. Cela nous conduit à l’une des principales fonctionnalités de WCF : vos services ne sont pas liés à une approche ou stratégie d’hébergement particulière.

[ASP.NET](http://www.asp.net/) est un framework web. Il a plusieurs éléments distincts qui servent à créer des applications web modernes et à hautes performances. 

- [ASP.NET Web Forms](http://www.asp.net/web-forms) vous permet de générer une interface utilisateur de bureau basée sur des formulaires plutôt que sur des données plus rapidement que la plupart des autres technologies web, grâce à un concepteur qui facilite les opérations de glisser-déplacer des contrôles web. 
- [ASP.NET MVC](http://www.asp.net/mvc) offre un meilleur contrôle de l’ensemble du pipeline web, depuis la couche HTTP jusqu’à l’interface utilisateur. 
- L’[API web ASP.NET](http://www.asp.net/web-api) est un framework basé sur une convention qui permet de créer des services REST. 
- [SignalR](http://www.asp.net/signalr) vous permet de fournir des communications selon le modèle push à vos applications web à l’aide du protocole [WebSocket](https://en.wikipedia.org/wiki/WebSocket).

### <a name="net-native"></a>.NET Native

.NET Native est un ensemble d’outils de génération natifs pour .NET Core. .NET Native est une chaîne d’outils Ahead-of-Time (AOT) qui produit des applications natives en compilant le code d’octet de langage intermédiaire en code machine natif. Cela signifie que le binaire obtenu est ce que le système d’exploitation exécute ; il n’y a pas de compilation JIT ou au moment de l’exécution. Il en résulte de meilleures performances de démarrage, ainsi que des avantages en termes de sécurité.

.NET Native est principalement utilisé par les applications .NET de la [Plateforme Windows universelle](https://msdn.microsoft.com/library/windows/apps/dn726767.aspx).

### <a name="mono"></a>Mono

[Mono](http://www.mono-project.com/docs/about-mono/) est l’implémentation open source et multiplateforme d’origine de .NET de la communauté [Mono Project](http://mono-project.com). Elle est désormais promue par Microsoft. Elle peut être considérée comme une version ouverte et multiplateforme du .NET Framework. Ses API suivent la progression du .NET Framework, pas de .NET Core.

Mono comprend plusieurs composants :

**Compilateur C#** : le compilateur C# de Mono est opérationnel pour C# 6.

**Runtime Mono** : le runtime implémente l’infrastructure ECMA CLI (Common Language Infrastructure). Le runtime fournit un compilateur juste-à-temps (JIT), un compilateur AOT (Ahead-of-Time), un chargeur de bibliothèque, le garbage collector, un système de thread et des fonctionnalités d’interopérabilité.

**Bibliothèque de classes de base** : la plateforme Mono fournit un ensemble complet de classes à utiliser comme fondations pour générer des applications. Ces classes sont compatibles avec les classes .Net Framework de Microsoft.

**Bibliothèque de classes Mono** : Mono fournit également plusieurs classes qui vont au-delà de la bibliothèque de classes de base fournie par le .NET Framework. Ces classes fournissent des fonctionnalités supplémentaires qui sont utiles, en particulier pour générer des applications Linux. À titre d’exemple, citons les classes pour Gtk+, les fichiers Zip, LDAP, OpenGL, Cairo et POSIX.

### <a name="xamarin-sdk"></a>SDK Xamarin

Le [SDK Xamarin](http://open.xamarin.com) est utilisé pour générer des applications mobiles et d’appareil natives, principalement pour les écosystèmes Apple et Google. Il est basé sur Mono et est open source sous licence MIT. Vous pouvez l’utiliser pour générer des applications iOS et Android pour téléphones, tablettes et montres. [Xamarin.Forms](https://www.xamarin.com/forms) est largement utilisé pour écrire des interfaces utilisateur réutilisables entre applications Apple, Google et Windows.

- En savoir plus sur le [SDK Xamarin](https://developer.xamarin.com/)
- [Télécharger Xamarin](https://www.xamarin.com/platform)



<!--HONumber=Nov16_HO1-->


