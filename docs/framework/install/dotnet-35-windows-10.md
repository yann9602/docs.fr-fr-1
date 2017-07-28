---
title: "Installer le .NET Framework 3.5 sur Windows 10, Windows 8.1 et Windows 8"
description: "Découvrez comment installer le .NET Framework 3.5 sur Windows 10, Windows 8.1 et Windows 8"
author: rlander
keywords: .NET Framework, installer
ms.date: 04/20/2017
ms.topic: article
ms.prod: .net-framework
ms.technology: vs-ide-deployment
ms.devlang: dotnet
ms.assetid: 67cda1d5-c6g4-4eb5-93e6-4f478de07ff7
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 64ba9cb408e565b20a001382c3b39a41602b6e55
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a>Installer le .NET Framework 3.5 sur Windows 10, Windows 8.1 et Windows 8

Le .NET Framework 3.5 peut être nécessaire pour exécuter une application sur Windows 10, Windows 8.1 et Windows 8. Vous pouvez également utiliser ces instructions pour les versions antérieures de Windows.

## <a name="install-the-net-framework-35-on-demand"></a>Installer .NET Framework 3.5 à la demande

Vous pouvez voir la boîte de dialogue de configuration suivante si vous essayez d’exécuter une application qui nécessite le .NET Framework 3.5. Choisissez **Installer cette fonctionnalité** pour activer le .NET Framework 3.5. Cette option requiert une connexion Internet.

![Boîte de dialogue d’installation du .NET Framework](./media/dotnet-framework-installation-dialog.jpg)

## <a name="enable-the-net-framework-35-in-control-panel"></a>Activer .NET Framework 3.5 dans le Panneau de configuration

Vous pouvez activer le .NET Framework 3.5 dans le Panneau de configuration de Windows. Cette option requiert une connexion Internet.

1. Appuyez sur la touche Windows ![logo Windows](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) de votre clavier, tapez « Fonctionnalités Windows » puis appuyez sur Entrée. La boîte de dialogue **Activer ou désactiver des fonctionnalités Windows** apparaît.

2. Cochez la case **.NET Framework 3.5 (inclut .NET 2.0 et 3.0)**, sélectionnez OK et redémarrez l’ordinateur si vous y êtes invité.

   ![Installation de .NET avec le Panneau de configuration](./media/dotnet-control-panel.png)

   Vous n’avez pas besoin de sélectionner des éléments enfants pour **Activation HTTP de Windows Communication Foundation** et **Activation non-HTTP de Windows Communication Foundation**, sauf si vous êtes un développeur ou un administrateur de serveur ayant besoin de cette fonctionnalité.

