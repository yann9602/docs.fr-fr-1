---
title: "Instructions relatives à l'hébergement dans les Services Internet (IIS)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de7dc897aa435d62c04c2e6a3ca82adf3a637a2a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="internet-information-service-hosting-instructions"></a><span data-ttu-id="8e811-102">Instructions relatives à l'hébergement dans les Services Internet (IIS)</span><span class="sxs-lookup"><span data-stu-id="8e811-102">Internet Information Service Hosting Instructions</span></span>
<span data-ttu-id="8e811-103">Pour exécuter les exemples hébergés par les services IIS (Internet Information Services), vous devez vous assurer que les services IIS sont correctement installés et en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="8e811-103">To run the samples that are hosted by Internet Information Services (IIS), you must make sure that IIS is properly installed and is running.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a><span data-ttu-id="8e811-104">Pour installer IIS version 7.5 sur Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="8e811-104">To install IIS version 7.5 on Windows Server 2008 R2</span></span>  
  
1.  <span data-ttu-id="8e811-105">À partir de **le Gestionnaire de serveur**, sélectionnez **rôles.**</span><span class="sxs-lookup"><span data-stu-id="8e811-105">From **Server Manager**, select **Roles.**</span></span> <span data-ttu-id="8e811-106">Sous **résumé des rôles**, cliquez sur **ajouter des rôles**.</span><span class="sxs-lookup"><span data-stu-id="8e811-106">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2.  <span data-ttu-id="8e811-107">Cliquez sur **suivant** pour afficher les **sélectionner des rôles de serveur** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="8e811-107">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3.  <span data-ttu-id="8e811-108">Sélectionnez **serveur d’applications** à partir de la **rôles** liste, puis cliquez sur **suivant** à deux reprises pour afficher le **sélectionner les Services de rôle** boîte de dialogue pour le Rôle de serveur d’applications.</span><span class="sxs-lookup"><span data-stu-id="8e811-108">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4.  <span data-ttu-id="8e811-109">Sélectionnez le **serveur Web (IIS)** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="8e811-109">Select the **Web Server (IIS)** check box.</span></span> <span data-ttu-id="8e811-110">Si vous êtes invité à installer les services de rôle supplémentaires et des fonctionnalités, cliquez sur **ajouter les fonctionnalités requises**.</span><span class="sxs-lookup"><span data-stu-id="8e811-110">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="8e811-111">Cliquez sur **suivant** à deux reprises pour afficher le **sélectionner les Services de rôle** boîte de dialogue pour le rôle serveur Web (IIS).</span><span class="sxs-lookup"><span data-stu-id="8e811-111">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5.  <span data-ttu-id="8e811-112">Développez **outils de gestion**, puis développez **IIS 6 Management Compatibility**.</span><span class="sxs-lookup"><span data-stu-id="8e811-112">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="8e811-113">Sélectionnez **outils de script 6 IIS**.</span><span class="sxs-lookup"><span data-stu-id="8e811-113">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="8e811-114">Si vous êtes invité à installer les services de rôle supplémentaires et des fonctionnalités, cliquez sur **ajouter des Services de rôle requis**.</span><span class="sxs-lookup"><span data-stu-id="8e811-114">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="8e811-115">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="8e811-115">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="8e811-116">Si l’aperçu des sélections est correct, cliquez sur **installer**.</span><span class="sxs-lookup"><span data-stu-id="8e811-116">If the summary of selections is correct, click **Install**.</span></span>  
  
7.  <span data-ttu-id="8e811-117">Lorsque l’installation est terminée, cliquez sur **fermer**.</span><span class="sxs-lookup"><span data-stu-id="8e811-117">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-7"></a><span data-ttu-id="8e811-118">Pour installer IIS version 7.5 sur Windows 7</span><span class="sxs-lookup"><span data-stu-id="8e811-118">To install IIS version 7.5 on Windows 7</span></span>  
  
1.  <span data-ttu-id="8e811-119">Cliquez sur **Démarrer**, puis cliquez sur **le panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="8e811-119">Click **Start**, and then click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="8e811-120">Ouvrez le **programmes** groupe.</span><span class="sxs-lookup"><span data-stu-id="8e811-120">Open the **Programs** group.</span></span>  
  
3.  <span data-ttu-id="8e811-121">Sous **programmes et fonctionnalités**, cliquez sur **activer ou désactiver des fonctionnalités Windows**.</span><span class="sxs-lookup"><span data-stu-id="8e811-121">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4.  <span data-ttu-id="8e811-122">Le **contrôle de compte d’utilisateur** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="8e811-122">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="8e811-123">Cliquez sur **Continuer**.</span><span class="sxs-lookup"><span data-stu-id="8e811-123">Click **Continue**.</span></span>  
  
5.  <span data-ttu-id="8e811-124">Le **des fonctionnalités Windows** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="8e811-124">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="8e811-125">Développez l’élément **Internet Information Services**.</span><span class="sxs-lookup"><span data-stu-id="8e811-125">Expand the item labeled **Internet Information Services**.</span></span>  
  
6.  <span data-ttu-id="8e811-126">Développez l’élément **Services World Wide Web**.</span><span class="sxs-lookup"><span data-stu-id="8e811-126">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7.  <span data-ttu-id="8e811-127">Développez l’élément **fonctionnalités de développement d’applications**.</span><span class="sxs-lookup"><span data-stu-id="8e811-127">Expand the item labeled **Application Development Features**.</span></span>  
  
8.  <span data-ttu-id="8e811-128">Assurez-vous que les éléments suivants sont sélectionnés :</span><span class="sxs-lookup"><span data-stu-id="8e811-128">Make sure the following items are selected:</span></span>  
  
    1.  <span data-ttu-id="8e811-129">**Extensibilité .NET**</span><span class="sxs-lookup"><span data-stu-id="8e811-129">**.NET Extensibility**</span></span>  
  
    2.  <span data-ttu-id="8e811-130">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="8e811-130">**ASP.NET**</span></span>  
  
    3.  <span data-ttu-id="8e811-131">**Extensions ISAPI**</span><span class="sxs-lookup"><span data-stu-id="8e811-131">**ISAPI Extensions**</span></span>  
  
    4.  <span data-ttu-id="8e811-132">**Filtres ISAPI**</span><span class="sxs-lookup"><span data-stu-id="8e811-132">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="8e811-133">Sous l’élément **Services World Wide Web**, développez **fonctionnalités Http communes**.</span><span class="sxs-lookup"><span data-stu-id="8e811-133">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
10. <span data-ttu-id="8e811-134">Assurez-vous que **contenu statique** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="8e811-134">Make sure **Static Content** is selected.</span></span>  
  
11. <span data-ttu-id="8e811-135">Sous l’élément **Services World Wide Web**, développez **sécurité**.</span><span class="sxs-lookup"><span data-stu-id="8e811-135">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
12. <span data-ttu-id="8e811-136">Assurez-vous que **l’authentification Windows** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="8e811-136">Make sure that **Windows Authentication** is selected.</span></span>  
  
13. <span data-ttu-id="8e811-137">Sous le **Internet Information Services** directory, développez l’élément **outils d’administration Web**, puis sélectionnez **Console de gestion IIS**.</span><span class="sxs-lookup"><span data-stu-id="8e811-137">Under the **Internet Information Services** directory, expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
14. <span data-ttu-id="8e811-138">Développez l’élément **IIS 6 Management Compatibility**, puis sélectionnez **outils de script IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="8e811-138">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="8e811-139">Sous le **Internet Information Services** directory, développez l’élément **Microsoft .NET Framework 3.5.1**, puis sélectionnez **Activation Http de Windows Communication Foundation**.</span><span class="sxs-lookup"><span data-stu-id="8e811-139">Under the **Internet Information Services** directory, expand the item labeled **Microsoft .NET Framework 3.5.1**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="8e811-140">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8e811-140">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a><span data-ttu-id="8e811-141">Pour installer IIS version 7.0 sur Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="8e811-141">To install IIS version 7.0 on Windows Server 2008</span></span>  
  
1.  <span data-ttu-id="8e811-142">À partir de **le Gestionnaire de serveur**, sélectionnez **rôles**.</span><span class="sxs-lookup"><span data-stu-id="8e811-142">From **Server Manager**, select **Roles**.</span></span> <span data-ttu-id="8e811-143">Sous **résumé des rôles**, cliquez sur **ajouter des rôles**.</span><span class="sxs-lookup"><span data-stu-id="8e811-143">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2.  <span data-ttu-id="8e811-144">Cliquez sur **suivant** pour afficher les **sélectionner des rôles de serveur** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="8e811-144">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3.  <span data-ttu-id="8e811-145">Sélectionnez **serveur d’applications** à partir de la **rôles** liste, puis cliquez sur **suivant** à deux reprises pour afficher le **sélectionner les Services de rôle** boîte de dialogue pour le Rôle de serveur d’applications.</span><span class="sxs-lookup"><span data-stu-id="8e811-145">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4.  <span data-ttu-id="8e811-146">Sélectionnez **serveur Web (IIS)** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="8e811-146">Select **Web Server (IIS)** check box.</span></span> <span data-ttu-id="8e811-147">Si vous êtes invité à installer les services de rôle supplémentaires et des fonctionnalités, cliquez sur **ajouter les fonctionnalités requises**.</span><span class="sxs-lookup"><span data-stu-id="8e811-147">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="8e811-148">Cliquez sur **suivant** à deux reprises pour afficher le **sélectionner les Services de rôle** boîte de dialogue pour le rôle serveur Web (IIS).</span><span class="sxs-lookup"><span data-stu-id="8e811-148">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5.  <span data-ttu-id="8e811-149">Développez **outils de gestion**, puis développez **IIS 6 Management Compatibility**.</span><span class="sxs-lookup"><span data-stu-id="8e811-149">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="8e811-150">Sélectionnez **outils de script 6 IIS**.</span><span class="sxs-lookup"><span data-stu-id="8e811-150">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="8e811-151">Si vous êtes invité à installer les services de rôle supplémentaires et des fonctionnalités, cliquez sur **ajouter des Services de rôle requis**.</span><span class="sxs-lookup"><span data-stu-id="8e811-151">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="8e811-152">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="8e811-152">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="8e811-153">Si l’aperçu des sélections est correct, cliquez sur **installer**.</span><span class="sxs-lookup"><span data-stu-id="8e811-153">If the summary of selections is correct, click **Install**.</span></span>  
  
7.  <span data-ttu-id="8e811-154">Lorsque l’installation est terminée, cliquez sur **fermer**.</span><span class="sxs-lookup"><span data-stu-id="8e811-154">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a><span data-ttu-id="8e811-155">Pour installer IIS version 7.0 sur Windows Vista</span><span class="sxs-lookup"><span data-stu-id="8e811-155">To install IIS version 7.0 on Windows Vista</span></span>  
  
1.  <span data-ttu-id="8e811-156">Cliquez sur Démarrer, puis sur Panneau de configuration.</span><span class="sxs-lookup"><span data-stu-id="8e811-156">Click Start, and then click Control Panel.</span></span>  
  
2.  <span data-ttu-id="8e811-157">Sélectionnez le **programmes** groupe.</span><span class="sxs-lookup"><span data-stu-id="8e811-157">Select the **Programs** group.</span></span>  
  
3.  <span data-ttu-id="8e811-158">Sous **programmes et fonctionnalités**, cliquez sur **activer ou désactiver des fonctionnalités Windows**.</span><span class="sxs-lookup"><span data-stu-id="8e811-158">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4.  <span data-ttu-id="8e811-159">Le **contrôle de compte d’utilisateur** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="8e811-159">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="8e811-160">Cliquez sur **Continuer**.</span><span class="sxs-lookup"><span data-stu-id="8e811-160">Click **Continue**.</span></span>  
  
5.  <span data-ttu-id="8e811-161">Le **des fonctionnalités Windows** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="8e811-161">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="8e811-162">Développez l’élément **Internet Information Services**.</span><span class="sxs-lookup"><span data-stu-id="8e811-162">Expand the item labeled **Internet Information Services**.</span></span>  
  
6.  <span data-ttu-id="8e811-163">Développez l’élément **Services World Wide Web**.</span><span class="sxs-lookup"><span data-stu-id="8e811-163">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7.  <span data-ttu-id="8e811-164">Développez l’élément **fonctionnalités de développement d’applications**.</span><span class="sxs-lookup"><span data-stu-id="8e811-164">Expand the item labeled **Application Development Features**.</span></span>  
  
8.  <span data-ttu-id="8e811-165">Assurez-vous que les éléments suivants sont sélectionnés :</span><span class="sxs-lookup"><span data-stu-id="8e811-165">Make sure the following items are selected:</span></span>  
  
    1.  <span data-ttu-id="8e811-166">**Extensibilité .NET**</span><span class="sxs-lookup"><span data-stu-id="8e811-166">**.NET Extensibility**</span></span>  
  
    2.  <span data-ttu-id="8e811-167">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="8e811-167">**ASP.NET**</span></span>  
  
    3.  <span data-ttu-id="8e811-168">**Extensions ISAPI**</span><span class="sxs-lookup"><span data-stu-id="8e811-168">**ISAPI Extensions**</span></span>  
  
    4.  <span data-ttu-id="8e811-169">**Filtres ISAPI**</span><span class="sxs-lookup"><span data-stu-id="8e811-169">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="8e811-170">Développez l’élément **outils d’administration Web**, puis sélectionnez **Console de gestion IIS**.</span><span class="sxs-lookup"><span data-stu-id="8e811-170">Expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
10. <span data-ttu-id="8e811-171">Sous l’élément **Services World Wide Web**, développez **fonctionnalités Http communes**.</span><span class="sxs-lookup"><span data-stu-id="8e811-171">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
11. <span data-ttu-id="8e811-172">Assurez-vous que **contenu statique** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="8e811-172">Make sure **Static Content** is selected.</span></span>  
  
12. <span data-ttu-id="8e811-173">Sous l’élément **Services World Wide Web**, développez **sécurité**.</span><span class="sxs-lookup"><span data-stu-id="8e811-173">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
13. <span data-ttu-id="8e811-174">Assurez-vous que **l’authentification Windows** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="8e811-174">Make sure **Windows Authentication** is selected.</span></span>  
  
14. <span data-ttu-id="8e811-175">Développez l’élément **IIS 6 Management Compatibility**, puis sélectionnez **outils de script IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="8e811-175">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="8e811-176">Développez l’élément **Microsoft .NET Framework 3.0**, puis sélectionnez **Activation Http de Windows Communication Foundation**.</span><span class="sxs-lookup"><span data-stu-id="8e811-176">Expand the item labeled **Microsoft .NET Framework 3.0**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="8e811-177">Cliquez sur**OK**.</span><span class="sxs-lookup"><span data-stu-id="8e811-177">Click**OK**.</span></span>  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a><span data-ttu-id="8e811-178">Pour installer IIS version 6.0 sur Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="8e811-178">To install IIS version 6.0 on Windows Server 2003</span></span>  
  
1.  <span data-ttu-id="8e811-179">À partir de **gérer votre serveur**, cliquez sur **ajouter ou supprimer un rôle**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8e811-179">From **Manage Your Server**, click **Add or remove a role**, and then click **Next**.</span></span>  
  
2.  <span data-ttu-id="8e811-180">Sélectionnez **serveur d’applications (IIS, ASP.NET)** à partir de la **rôle serveur** liste, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8e811-180">Select **Application server (IIS, ASP.NET)** from the **Server Role** list, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="8e811-181">Sélectionnez **activer ASP.NET** case à cocher, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8e811-181">Select **Enable ASP.NET** check box, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="8e811-182">Si l'aperçu des sélections est correct, cliquez sur Suivant.</span><span class="sxs-lookup"><span data-stu-id="8e811-182">If the summary of selections is correct, click Next.</span></span>  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a><span data-ttu-id="8e811-183">Pour installer IIS version 5.1 sur Windows XP avec Service Pack 2 et Service Pack 3 installés</span><span class="sxs-lookup"><span data-stu-id="8e811-183">To install IIS version 5.1 on Windows XP with Service Pack 2 and Service Pack 3 installed</span></span>  
  
1.  <span data-ttu-id="8e811-184">Dans le panneau de configuration, cliquez sur **Ajout / Suppression de programmes**.</span><span class="sxs-lookup"><span data-stu-id="8e811-184">In Control Panel, click **Add or Remove Programs**.</span></span>  
  
2.  <span data-ttu-id="8e811-185">Dans le **Ajout / Suppression de programmes** boîte de dialogue, cliquez sur **ajouter/supprimer des composants Windows**.</span><span class="sxs-lookup"><span data-stu-id="8e811-185">In the **Add or Remove Programs** dialog box, click **Add/Remove Windows Components**.</span></span>  
  
3.  <span data-ttu-id="8e811-186">Dans le **Assistant Composants de Windows**, sélectionnez le **Internet Information Services (IIS)** case à cocher, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8e811-186">In the **Windows Components Wizard**, select the **Internet Information Services (IIS)** check box, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="8e811-187">Si le **fichiers nécessaires** boîte de dialogue s’affiche, insérez le disque d’installation de système d’exploitation, accédez au dossier i386, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8e811-187">If the **Files Needed** dialog box is displayed, insert your operating system installation disc, browse to the i386 folder, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="8e811-188">Lorsque l’installation est terminée, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="8e811-188">When installation completes, click **Finish**.</span></span>  
  
6.  <span data-ttu-id="8e811-189">Fermer le **Ajout / Suppression de programmes** boîte de dialogue et fermez **le panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="8e811-189">Close the **Add or Remove Programs** dialog box, and then close **Control Panel**.</span></span>  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a><span data-ttu-id="8e811-190">Pour vérifier l'installation d'IIS et d'ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8e811-190">To verify the installation of IIS and ASP.NET</span></span>  
  
1.  <span data-ttu-id="8e811-191">Enregistrez le fichier HTML indiqué à la fin de cette rubrique dans le répertoire \InetPub\wwwroot racine et nommez-le Default.aspx.</span><span class="sxs-lookup"><span data-stu-id="8e811-191">Save the HTML file found at the end of this topic in the root \InetPub\wwwroot directory and name it Default.aspx.</span></span>  
  
2.  <span data-ttu-id="8e811-192">Ouvrez une nouvelle fenêtre de navigateur.</span><span class="sxs-lookup"><span data-stu-id="8e811-192">Open a browser window.</span></span>  
  
3.  <span data-ttu-id="8e811-193">Type `http://localhost/Default.aspx` dans la zone d’adresse et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="8e811-193">Type `http://localhost/Default.aspx` in the address box, and then press ENTER.</span></span>  
  
4.  <span data-ttu-id="8e811-194">Une page web contenant le texte « Hello World » doit apparaître.</span><span class="sxs-lookup"><span data-stu-id="8e811-194">A Web page with the text "Hello World" should appear.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e811-195">Chaque fois que vous installez une nouvelle version du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], vous devez réinscrire aspnet_isapi comme extension de service Web pour IIS.</span><span class="sxs-lookup"><span data-stu-id="8e811-195">Each time you install a new version of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], you must re-register aspnet_isapi as a Web service extension for IIS.</span></span> <span data-ttu-id="8e811-196">Pour ce faire, émettez la commande `aspnet_regiis –I –enable`.</span><span class="sxs-lookup"><span data-stu-id="8e811-196">To do so, issue the `aspnet_regiis –I –enable` command.</span></span>  
  
## <a name="sample-code"></a><span data-ttu-id="8e811-197">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="8e811-197">Sample Code</span></span>  
  
```xml  
<html>  
   <body>  
       <form >  
           <h3> Hello World  
           </h3>  
       </form>  
   </body>  
</html>  
```
