---
title: "Installer le .NET Framework sur Windows 10"
description: "Découvrez comment installer le .NET Framework sur Windows 10 ou Windows Server 2016."
author: rlander
ms.author: mairaw
keywords: .NET Framework, installer
ms.date: 11/17/2017
ms.topic: article
ms.custom: updateeachrelease
ms.prod: .net-framework
ms.openlocfilehash: d7f8dd4c6ee9f7eeda389a955f806a5765876ea7
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2017
---
# <a name="install-the-net-framework-on-windows-10-and-windows-server-2016"></a>Installer le .NET Framework sur Windows 10 et Windows Server 2016

Le .NET Framework est requis pour exécuter des applications sur Windows. Les instructions fournies dans cet article devraient vous aider à installer les versions du .NET Framework dont vous avez besoin. Le [.NET Framework 4.7.1](https://www.microsoft.com/download/details.aspx?id=56115&desc=dotnet47) est la dernière version disponible.

Vous arrivées sur cette page après la tentative d’exécution d’une application et afficher une boîte de dialogue sur votre ordinateur semblable à la suivante :

![Cette application n’a pas pu être démarrée.](./media/this-application-could-not-be-started.png)

## <a name="net-framework-471"></a>.NET framework 4.7.1

Le Kit de développement .NET Framework 4.7.1 est inclus dans :

* [Mise à jour Windows 10 automne créateurs (version 1709)](https://www.microsoft.com/software-download/windows10)
* [Windows Server 2016 (version 1709)](https://docs.microsoft.com/windows-server/get-started/get-started-with-1709)

> [!div class="button"]
[Télécharger .NET Framework 4.7.1](https://www.microsoft.com/net/download/thank-you/net471?utm_source=ms-docs&utm_medium=referral)

Le [.NET Framework 4.7.1](https://www.microsoft.com/download/details.aspx?id=56115&desc=dotnet47) peut être utilisé pour exécuter des applications créées pour le .NET Framework 4.0 via 4.7.1.

Vous pouvez installer le [.NET Framework 4.7.1](https://www.microsoft.com/en-us/download/details.aspx?id=56115&desc=dotnet47) sur :

* Mise à jour de créateurs de Windows 10 (version 1703)
* Mise à jour de la date anniversaire Windows 10 (version 1607)
* Windows Server 2016

Le .NET Framework 4.7.1 n’est pas pris en charge sur :

* Windows 10 1507
* Windows 10 1511

Si vous utilisez Windows 10 1507 ou 1511 et que vous souhaitez installer le .NET Framework 4.7.1, vous devez tout d’abord mettre à niveau vers une version ultérieure de Windows 10.

## <a name="net-framework-461"></a>.NET Framework 4.6.1

Le [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) est la dernière version prise en charge .NET Framework sur Windows 10 1507 et 1511.

Le .NET Framework 4.6.1 prend en charge les applications conçues pour le .NET Framework 4.0 via 4.6.1.

## <a name="net-framework-35"></a>.NET Framework 3.5

Suivez les instructions pour installer le [.NET Framework 3.5 sur Windows 10](dotnet-35-windows-10.md).

Le .NET Framework 3.5 prend en charge les applications conçues pour le .NET Framework 1.0 à 3.5.

## <a name="additional-information"></a>Informations supplémentaires

Versions du .NET framework 4.x sont mises à jour sur place pour les versions antérieures. Cela signifie que les éléments suivants :

- Vous ne pouvez avoir qu’une seule version du .NET Framework 4.x installés sur votre ordinateur.

- Si une version ultérieure est déjà installée, vous ne pouvez pas installer une version antérieure du .NET Framework sur votre ordinateur.

- les versions du .NET Framework 4.x peuvent servir à exécuter des applications créées pour le .NET Framework 4.0 via cette version. Par exemple, .NET Framework 4.7 peut être utilisé pour exécuter des applications créées pour le .NET Framework 4.0 via 4.7. La dernière version (.NET Framework 4.7.1) permet d’exécution des applications générées toutes les versions du .NET Framework 4.0 à compter.

Pour obtenir la liste de toutes les versions du .NET Framework disponibles au téléchargement, consultez le [téléchargements .NET](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral) page.

## <a name="help"></a>Help

Si vous ne peut pas obtenir la version correcte du .NET Framework est installé, vous pouvez [contactez Microsoft pour l’aide](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help).

## <a name="see-also"></a>Voir aussi

[Téléchargements de .NET](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral)   
[Résolution des problèmes liés aux installations et désinstallations bloquées du .NET Framework](troubleshoot-blocked-installations-and-uninstallations.md)   
[Installer le .NET Framework pour les développeurs](guide-for-developers.md)