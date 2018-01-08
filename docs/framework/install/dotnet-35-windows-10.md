---
title: "Installer le .NET Framework 3.5 sur Windows 10, Windows 8.1 et Windows 8"
description: "Découvrez comment installer .NET Framework 3.5 sur Windows 10, Windows 8.1 et Windows 8."
author: rlander
ms.author: mairaw
ms.date: 11/27/2017
ms.topic: article
ms.prod: .net-framework
ms.workload: dotnet
ms.openlocfilehash: ca56bfb37cee60ab014dada7b5d72b74b375dd7f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a><span data-ttu-id="82f04-103">Installer le .NET Framework 3.5 sur Windows 10, Windows 8.1 et Windows 8</span><span class="sxs-lookup"><span data-stu-id="82f04-103">Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8</span></span>

<span data-ttu-id="82f04-104">Vous pouvez avoir besoin de .NET Framework 3.5 pour exécuter une application sur Windows 10, Windows 8.1 et Windows 8.</span><span class="sxs-lookup"><span data-stu-id="82f04-104">You may need the .NET Framework 3.5 to run an app on Windows 10, Windows 8.1, and Windows 8.</span></span> <span data-ttu-id="82f04-105">Vous pouvez également utiliser ces instructions pour les versions antérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="82f04-105">You can also use these instructions for earlier Windows versions.</span></span>

## <a name="install-the-net-framework-35-on-demand"></a><span data-ttu-id="82f04-106">Installer .NET Framework 3.5 à la demande</span><span class="sxs-lookup"><span data-stu-id="82f04-106">Install the .NET Framework 3.5 on Demand</span></span>

<span data-ttu-id="82f04-107">Vous pouvez voir la boîte de dialogue de configuration suivante si vous essayez d’exécuter une application qui nécessite .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="82f04-107">You may see the following configuration dialog if you try to run an app that requires the .NET Framework 3.5.</span></span> <span data-ttu-id="82f04-108">Choisissez **Installer cette fonctionnalité** pour activer le .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="82f04-108">Choose **Install this feature** to enable the .NET Framework 3.5.</span></span> <span data-ttu-id="82f04-109">Cette option requiert une connexion Internet.</span><span class="sxs-lookup"><span data-stu-id="82f04-109">This option requires an Internet connection.</span></span>

![Boîte de dialogue d’installation du .NET Framework](./media/dotnet-framework-installation-dialog.jpg)

## <a name="enable-the-net-framework-35-in-control-panel"></a><span data-ttu-id="82f04-111">Activer .NET Framework 3.5 dans le Panneau de configuration</span><span class="sxs-lookup"><span data-stu-id="82f04-111">Enable the .NET Framework 3.5 in Control Panel</span></span>

<span data-ttu-id="82f04-112">Vous pouvez activer le .NET Framework 3.5 dans le Panneau de configuration de Windows.</span><span class="sxs-lookup"><span data-stu-id="82f04-112">You can enable the .NET Framework 3.5 through the Windows Control Panel.</span></span> <span data-ttu-id="82f04-113">Cette option requiert une connexion Internet.</span><span class="sxs-lookup"><span data-stu-id="82f04-113">This option requires an Internet connection.</span></span>

1. <span data-ttu-id="82f04-114">Appuyez sur la touche Windows ![logo Windows](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) de votre clavier, tapez « Fonctionnalités Windows » puis appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="82f04-114">Press the Windows key Windows ![Windows logo](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) on your keyboard, type "Windows Features", and press Enter.</span></span> <span data-ttu-id="82f04-115">La boîte de dialogue **Activer ou désactiver des fonctionnalités Windows** apparaît.</span><span class="sxs-lookup"><span data-stu-id="82f04-115">The **Turn Windows features on or off** dialog box appears.</span></span>

2. <span data-ttu-id="82f04-116">Cochez la case **.NET Framework 3.5 (inclut .NET 2.0 et 3.0)**, sélectionnez **OK** et redémarrez l’ordinateur si vous y êtes invité.</span><span class="sxs-lookup"><span data-stu-id="82f04-116">Select the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box, select **OK**, and reboot your computer if prompted.</span></span>

   ![Installation de .NET avec le Panneau de configuration](./media/dotnet-control-panel.png)

   <span data-ttu-id="82f04-118">Vous n’avez pas besoin de sélectionner des éléments enfants pour **Activation HTTP de Windows Communication Foundation** et **Activation non-HTTP de Windows Communication Foundation**, sauf si vous êtes un développeur ou un administrateur de serveur ayant besoin de cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="82f04-118">You don't need to select the child items for **Windows Communication Foundation (WCF) HTTP Activation** and **Windows Communication Foundation (WCF) Non-HTTP Activation** unless you're a developer or server administrator who requires this functionality.</span></span>

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a><span data-ttu-id="82f04-119">Résoudre les problèmes d’installation du .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="82f04-119">Troubleshoot the installation of the .NET Framework 3.5</span></span>

<span data-ttu-id="82f04-120">Pendant l’installation, si vous rencontrez l’erreur 0x800f0906, 0x800f0907, 0x800f081f ou 0x800F0922, consultez [Erreur d’installation de .NET Framework 3.5 : 0x800f0906, 0x800f0907 ou 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) pour découvrir comment résoudre ces problèmes.</span><span class="sxs-lookup"><span data-stu-id="82f04-120">During installation, you may encounter error 0x800f0906, 0x800f0907, 0x800f081f, or 0x800F0922, in which case refer to [.NET Framework 3.5 installation error: 0x800f0906, 0x800f0907, or 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) to see how to resolve these issues.</span></span>

<span data-ttu-id="82f04-121">Si l’une des méthodes décrites dans l’article précédent échoue ou que vous n’avez pas de connexion Internet, vous devez utiliser votre support d’installation Windows.</span><span class="sxs-lookup"><span data-stu-id="82f04-121">If any of the methods discussed in the previous article fail or if you don't have an Internet connection, it's necessary to use your Windows installation media.</span></span> <span data-ttu-id="82f04-122">Pour plus d’informations, consultez [Déployer le .NET Framework 3.5 à l’aide de Gestion et maintenance des images de déploiement (DISM)](https://technet.microsoft.com/library/Dn482069.aspx).</span><span class="sxs-lookup"><span data-stu-id="82f04-122">For more information, see [Deploy .NET Framework 3.5 by using Deployment Image Servicing and Management (DISM)](https://technet.microsoft.com/library/Dn482069.aspx).</span></span> <span data-ttu-id="82f04-123">Si vous ne disposez pas du support d’installation, consultez [Créer un support d’installation pour Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).</span><span class="sxs-lookup"><span data-stu-id="82f04-123">If you don't have the installation media, see [Create installation media for Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).</span></span>