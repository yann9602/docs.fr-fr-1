---
title: "Installer le .NET Framework 3.5 sur Windows 10, Windows 8.1 et Windows 8"
description: "Découvrez comment installer .NET Framework 3.5 sur Windows 10, Windows 8.1 et Windows 8."
author: rlander
ms.author: mairaw
keywords: .NET Framework, installer
ms.date: 05/26/2017
ms.topic: article
ms.prod: .net-framework
ms.technology: vs-ide-deployment
ms.devlang: dotnet
ms.assetid: 67cda1d5-c6g4-4eb5-93e6-4f478de07ff7
ms.translationtype: HT
ms.sourcegitcommit: 21c6a1485f3d0c38bde065d6ecc7b07d5e424c1d
ms.openlocfilehash: 85a3cada074714c24015d90c26d94551f4f411f2
ms.contentlocale: fr-fr
ms.lasthandoff: 08/05/2017

---

# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a>Installer le .NET Framework 3.5 sur Windows 10, Windows 8.1 et Windows 8

Vous pouvez avoir besoin de .NET Framework 3.5 pour exécuter une application sur Windows 10, Windows 8.1 et Windows 8. Vous pouvez également utiliser ces instructions pour les versions antérieures de Windows.

## <a name="install-the-net-framework-35-on-demand"></a>Installer .NET Framework 3.5 à la demande

Vous pouvez voir la boîte de dialogue de configuration suivante si vous essayez d’exécuter une application qui nécessite .NET Framework 3.5. Choisissez **Installer cette fonctionnalité** pour activer le .NET Framework 3.5. Cette option requiert une connexion Internet.

![Boîte de dialogue d’installation du .NET Framework](./media/dotnet-framework-installation-dialog.jpg)

## <a name="enable-the-net-framework-35-in-control-panel"></a>Activer .NET Framework 3.5 dans le Panneau de configuration

Vous pouvez activer le .NET Framework 3.5 dans le Panneau de configuration de Windows. Cette option requiert une connexion Internet.

1. Appuyez sur la touche Windows ![logo Windows](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) de votre clavier, tapez « Fonctionnalités Windows » puis appuyez sur Entrée. La boîte de dialogue **Activer ou désactiver des fonctionnalités Windows** apparaît.

2. Cochez la case **.NET Framework 3.5 (inclut .NET 2.0 et 3.0)**, sélectionnez **OK** et redémarrez l’ordinateur si vous y êtes invité.

   ![Installation de .NET avec le Panneau de configuration](./media/dotnet-control-panel.png)

   Vous n’avez pas besoin de sélectionner des éléments enfants pour **Activation HTTP de Windows Communication Foundation** et **Activation non-HTTP de Windows Communication Foundation**, sauf si vous êtes un développeur ou un administrateur de serveur ayant besoin de cette fonctionnalité.

