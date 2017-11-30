---
title: Installation de Message Queuing (MSMQ)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 89d81a25da6494fc9cbf041ae68f2985b5c90a81
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="installing-message-queuing-msmq"></a><span data-ttu-id="2abaf-102">Installation de Message Queuing (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="2abaf-102">Installing Message Queuing (MSMQ)</span></span>
<span data-ttu-id="2abaf-103">Les procédures suivantes indiquent comment installer Message Queuing 4.0 et Message Queuing 3.0.</span><span class="sxs-lookup"><span data-stu-id="2abaf-103">The following procedures show how to install Message Queuing 4.0 and Message Queuing 3.0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2abaf-104">Message Queuing 4.0 n'est pas disponible dans [!INCLUDE[wxp](../../../../includes/wxp-md.md)] et [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2abaf-104">Message Queuing 4.0 is not available in [!INCLUDE[wxp](../../../../includes/wxp-md.md)] and [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a><span data-ttu-id="2abaf-105">Pour installer Message Queuing 4.0 sur Windows Server 2008 ou Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="2abaf-105">To install Message Queuing 4.0 on Windows Server 2008 or Windows Server 2008 R2</span></span>  
  
1.  <span data-ttu-id="2abaf-106">Dans le Gestionnaire de serveur, cliquez sur **fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="2abaf-106">In Server Manager, click **Features**.</span></span>  
  
2.  <span data-ttu-id="2abaf-107">Dans le volet droit sous **résumé des fonctionnalités**, cliquez sur **ajouter des fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="2abaf-107">In the right-hand pane under **Features Summary**, click **Add Features**.</span></span>  
  
3.  <span data-ttu-id="2abaf-108">Dans la fenêtre résultante, développez **Message Queuing**.</span><span class="sxs-lookup"><span data-stu-id="2abaf-108">In the resulting window, expand **Message Queuing**.</span></span>  
  
4.  <span data-ttu-id="2abaf-109">Développez **Message Queuing Services**.</span><span class="sxs-lookup"><span data-stu-id="2abaf-109">Expand **Message Queuing Services**.</span></span>  
  
5.  <span data-ttu-id="2abaf-110">Cliquez sur **intégration des Services Active** (pour les ordinateurs joints à un domaine), puis cliquez sur **prise en charge HTTP**.</span><span class="sxs-lookup"><span data-stu-id="2abaf-110">Click **Directory Services Integration** (for computers joined to a Domain), then click **HTTP Support**.</span></span>  
  
6.  <span data-ttu-id="2abaf-111">Cliquez sur **suivant**, puis cliquez sur **installer**.</span><span class="sxs-lookup"><span data-stu-id="2abaf-111">Click **Next**,then click **Install**.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a><span data-ttu-id="2abaf-112">Pour installer Message Queuing 4.0 sur Windows 7 ou Windows Vista</span><span class="sxs-lookup"><span data-stu-id="2abaf-112">To install Message Queuing 4.0 on Windows 7 or Windows Vista</span></span>  
  
1.  <span data-ttu-id="2abaf-113">Ouvrez le **Panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="2abaf-113">Open **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="2abaf-114">Cliquez sur **programmes** puis, sous **programmes et fonctionnalités**, cliquez sur **activer et désactiver des fonctionnalités Windows**.</span><span class="sxs-lookup"><span data-stu-id="2abaf-114">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
3.  <span data-ttu-id="2abaf-115">Développez Microsoft Message Queue Server (MSMQ), développez le noyau du serveur MSMQ (Microsoft Message Queue), puis cochez les cases des fonctionnalités Message Queuing à installer :</span><span class="sxs-lookup"><span data-stu-id="2abaf-115">Expand Microsoft Message Queue (MSMQ) Server, expand Microsoft Message Queue (MSMQ) Server Core, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
    -   <span data-ttu-id="2abaf-116">Intégration des services de domaine Active Directory MSMQ (pour les ordinateurs liés à un domaine).</span><span class="sxs-lookup"><span data-stu-id="2abaf-116">MSMQ Active Directory Domain Services Integration (for computers joined to a Domain).</span></span>  
  
    -   <span data-ttu-id="2abaf-117">Prise en charge HTTP MSMQ.</span><span class="sxs-lookup"><span data-stu-id="2abaf-117">MSMQ HTTP Support.</span></span>  
  
4.  <span data-ttu-id="2abaf-118">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2abaf-118">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="2abaf-119">Si vous êtes invité à redémarrer l’ordinateur, cliquez sur **OK** pour terminer l’installation.</span><span class="sxs-lookup"><span data-stu-id="2abaf-119">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a><span data-ttu-id="2abaf-120">Pour installer Message Queuing 3.0 sur Windows XP et Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="2abaf-120">To install Message Queuing 3.0 on Windows XP and Windows Server 2003</span></span>  
  
1.  <span data-ttu-id="2abaf-121">Ouvrez le **Panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="2abaf-121">Open **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="2abaf-122">Cliquez sur **Ajout/Suppression de programmes** puis cliquez sur **ajouter des composants Windows**.</span><span class="sxs-lookup"><span data-stu-id="2abaf-122">Click **Add Remove Programs** and then click **Add Windows Components**.</span></span>  
  
3.  <span data-ttu-id="2abaf-123">Sélectionnez Message Queuing, cliquez sur **détails**.</span><span class="sxs-lookup"><span data-stu-id="2abaf-123">Select Message Queuing and click **Details**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2abaf-124">Si vous exécutez [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], sélectionnez Serveur d'applications pour accéder à Message Queuing.</span><span class="sxs-lookup"><span data-stu-id="2abaf-124">If you are running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], select Application Server to access Message Queuing.</span></span>  
  
4.  <span data-ttu-id="2abaf-125">Vérifiez que l'option Prise en charge HTTP MSMQ est activée dans la page de détails.</span><span class="sxs-lookup"><span data-stu-id="2abaf-125">Ensure that the option MSMQ HTTP Support is selected on the details page.</span></span>  
  
5.  <span data-ttu-id="2abaf-126">Cliquez sur **OK** pour quitter la page de détails, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="2abaf-126">Click **OK** to exit the details page, and then click **Next**.</span></span> <span data-ttu-id="2abaf-127">Terminez l'installation.</span><span class="sxs-lookup"><span data-stu-id="2abaf-127">Complete the installation.</span></span>  
  
6.  <span data-ttu-id="2abaf-128">Si vous êtes invité à redémarrer l’ordinateur, cliquez sur **OK** pour terminer l’installation.</span><span class="sxs-lookup"><span data-stu-id="2abaf-128">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2abaf-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2abaf-129">See Also</span></span>  
 [<span data-ttu-id="2abaf-130">Instructions d’installation</span><span class="sxs-lookup"><span data-stu-id="2abaf-130">Set-Up Instructions</span></span>](../../../../docs/framework/wcf/samples/set-up-instructions.md)
