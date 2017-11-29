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
ms.openlocfilehash: 85a3cada074714c24015d90c26d94551f4f411f2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a><span data-ttu-id="3ad31-104">Installer le .NET Framework 3.5 sur Windows 10, Windows 8.1 et Windows 8</span><span class="sxs-lookup"><span data-stu-id="3ad31-104">Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8</span></span>

<span data-ttu-id="3ad31-105">Vous pouvez avoir besoin de .NET Framework 3.5 pour exécuter une application sur Windows 10, Windows 8.1 et Windows 8.</span><span class="sxs-lookup"><span data-stu-id="3ad31-105">You may need the .NET Framework 3.5 to run an app on Windows 10, Windows 8.1, and Windows 8.</span></span> <span data-ttu-id="3ad31-106">Vous pouvez également utiliser ces instructions pour les versions antérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="3ad31-106">You can also use these instructions for earlier Windows versions.</span></span>

## <a name="install-the-net-framework-35-on-demand"></a><span data-ttu-id="3ad31-107">Installer .NET Framework 3.5 à la demande</span><span class="sxs-lookup"><span data-stu-id="3ad31-107">Install the .NET Framework 3.5 on Demand</span></span>

<span data-ttu-id="3ad31-108">Vous pouvez voir la boîte de dialogue de configuration suivante si vous essayez d’exécuter une application qui nécessite .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="3ad31-108">You may see the following configuration dialog if you try to run an app that requires the .NET Framework 3.5.</span></span> <span data-ttu-id="3ad31-109">Choisissez **Installer cette fonctionnalité** pour activer le .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="3ad31-109">Choose **Install this feature** to enable the .NET Framework 3.5.</span></span> <span data-ttu-id="3ad31-110">Cette option requiert une connexion Internet.</span><span class="sxs-lookup"><span data-stu-id="3ad31-110">This option requires an Internet connection.</span></span>

![Boîte de dialogue d’installation du .NET Framework](./media/dotnet-framework-installation-dialog.jpg)

## <a name="enable-the-net-framework-35-in-control-panel"></a><span data-ttu-id="3ad31-112">Activer .NET Framework 3.5 dans le Panneau de configuration</span><span class="sxs-lookup"><span data-stu-id="3ad31-112">Enable the .NET Framework 3.5 in Control Panel</span></span>

<span data-ttu-id="3ad31-113">Vous pouvez activer le .NET Framework 3.5 dans le Panneau de configuration de Windows.</span><span class="sxs-lookup"><span data-stu-id="3ad31-113">You can enable the .NET Framework 3.5 through the Windows Control Panel.</span></span> <span data-ttu-id="3ad31-114">Cette option requiert une connexion Internet.</span><span class="sxs-lookup"><span data-stu-id="3ad31-114">This option requires an Internet connection.</span></span>

1. <span data-ttu-id="3ad31-115">Appuyez sur la touche Windows ![logo Windows](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) de votre clavier, tapez « Fonctionnalités Windows » puis appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="3ad31-115">Press the Windows key Windows ![Windows logo](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) on your keyboard, type "Windows Features", and press Enter.</span></span> <span data-ttu-id="3ad31-116">La boîte de dialogue **Activer ou désactiver des fonctionnalités Windows** apparaît.</span><span class="sxs-lookup"><span data-stu-id="3ad31-116">The **Turn Windows features on or off** dialog box appears.</span></span>

2. <span data-ttu-id="3ad31-117">Cochez la case **.NET Framework 3.5 (inclut .NET 2.0 et 3.0)**, sélectionnez **OK** et redémarrez l’ordinateur si vous y êtes invité.</span><span class="sxs-lookup"><span data-stu-id="3ad31-117">Select the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box, select **OK**, and reboot your computer if prompted.</span></span>

   ![Installation de .NET avec le Panneau de configuration](./media/dotnet-control-panel.png)

   <span data-ttu-id="3ad31-119">Vous n’avez pas besoin de sélectionner des éléments enfants pour **Activation HTTP de Windows Communication Foundation** et **Activation non-HTTP de Windows Communication Foundation**, sauf si vous êtes un développeur ou un administrateur de serveur ayant besoin de cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="3ad31-119">You don't need to select the child items for **Windows Communication Foundation (WCF) HTTP Activation** and **Windows Communication Foundation (WCF) Non-HTTP Activation** unless you're a developer or server administrator who requires this functionality.</span></span>
