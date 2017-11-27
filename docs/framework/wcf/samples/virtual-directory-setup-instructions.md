---
title: "Instructions d'installation du répertoire virtuel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
caps.latest.revision: "36"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b727f391abfeb1112de1b6cde3ceb564d3860974
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="virtual-directory-setup-instructions"></a><span data-ttu-id="6f873-102">Instructions d'installation du répertoire virtuel</span><span class="sxs-lookup"><span data-stu-id="6f873-102">Virtual Directory Setup Instructions</span></span>
<span data-ttu-id="6f873-103">Les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ont pour but de partager un répertoire virtuel commun nommé servicemodelsamples, mappé au dossier %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="6f873-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples are intended to share a common virtual directory named servicemodelsamples that is mapped to the %SystemDrive%\inetpub\wwwroot\servicemodelsamples folder.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f873-104">%SystemDrive% correspond généralement à C: ou D:, en fonction de l'emplacement de lecteur où Internet Information Services (IIS) est installé.</span><span class="sxs-lookup"><span data-stu-id="6f873-104">%SystemDrive% is usually C: or D:, depending on the drive location where Internet Information Services (IIS) is installed.</span></span>  
  
 <span data-ttu-id="6f873-105">Vous pouvez exécuter les fichiers Setupvroot.bat et Cleanupvroot.bat de la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) pour créer le répertoire virtuel.</span><span class="sxs-lookup"><span data-stu-id="6f873-105">You can run the Setupvroot.bat and Cleanupvroot.bat files from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) to create the virtual directory.</span></span> <span data-ttu-id="6f873-106">Si vous préférez créer le répertoire virtuel manuellement, exécutez les procédures suivantes.</span><span class="sxs-lookup"><span data-stu-id="6f873-106">If you prefer to create the virtual directory manually, use the following procedures.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="6f873-107">Procédures</span><span class="sxs-lookup"><span data-stu-id="6f873-107">Procedures</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a><span data-ttu-id="6f873-108">Pour créer un répertoire virtuel dans IIS 7.0 ou 7.5</span><span class="sxs-lookup"><span data-stu-id="6f873-108">To create a virtual directory in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="6f873-109">À partir de la **Démarrer** menu, cliquez sur **exécuter**, puis tapez **inetmgr** pour ouvrir le composant logiciel enfichable MMC Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="6f873-109">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2.  <span data-ttu-id="6f873-110">Dans le volet gauche, développez le nœud portant le nom d’ordinateur, puis le **Sites** nœud.</span><span class="sxs-lookup"><span data-stu-id="6f873-110">In the left pane, expand the node with the computer's name, and then expand the **Sites** node.</span></span>  
  
3.  <span data-ttu-id="6f873-111">Avec le bouton droit **Site Web par défaut**, puis sélectionnez **ajouter une Application** pour ouvrir le **fenêtre Ajouter l’Application**.</span><span class="sxs-lookup"><span data-stu-id="6f873-111">Right-click **Default Web Site**, and then select **Add Application** to open the **Add Application window**.</span></span>  
  
4.  <span data-ttu-id="6f873-112">Dans la fenêtre, tapez `servicemodelsamples` comme alias pour le répertoire virtuel que vous créez.</span><span class="sxs-lookup"><span data-stu-id="6f873-112">In the window, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5.  <span data-ttu-id="6f873-113">Créez le répertoire suivant : %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span><span class="sxs-lookup"><span data-stu-id="6f873-113">Create the following directory: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span></span>  
  
6.  <span data-ttu-id="6f873-114">Affectez la valeur %SystemDrive%\inetpub\wwwroot\servicemodelsamples au chemin d'accès physique.</span><span class="sxs-lookup"><span data-stu-id="6f873-114">Set the physical path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  <span data-ttu-id="6f873-115">La plupart des exemples WCF copient les fichiers exécutables de service dans cet emplacement une fois générés.</span><span class="sxs-lookup"><span data-stu-id="6f873-115">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
7.  <span data-ttu-id="6f873-116">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6f873-116">Click **OK**.</span></span> <span data-ttu-id="6f873-117">L'application Web est créée pour les exemples WCF.</span><span class="sxs-lookup"><span data-stu-id="6f873-117">The Web application is now created for the WCF samples.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6f873-118">Cette tâche doit être exécutée une seule fois, car les exemples [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilisent tous la même application Web (servicemodelsamples).</span><span class="sxs-lookup"><span data-stu-id="6f873-118">This task must be performed only once, because all of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples use the same servicemodelsamples Web application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6f873-119">Dans cette documentation, le terme `virtual directory` est synonyme du terme `Web application`.</span><span class="sxs-lookup"><span data-stu-id="6f873-119">For the purpose of this documentation, the term `virtual directory` is synonymous with `Web application`.</span></span>  
  
     <span data-ttu-id="6f873-120">Après avoir créé le répertoire virtuel, vous devez définir ses propriétés pour que les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] puissent être exécutés.</span><span class="sxs-lookup"><span data-stu-id="6f873-120">In addition to creating the virtual directory, you must also set its properties to enable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services to run.</span></span> <span data-ttu-id="6f873-121">Pour plus d'informations, consultez ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="6f873-121">See below for details.</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a><span data-ttu-id="6f873-122">Pour créer un répertoire virtuel dans IIS 5.1 ou 6.0 :</span><span class="sxs-lookup"><span data-stu-id="6f873-122">To create a virtual directory in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="6f873-123">Ouvrez une fenêtre d’invite de commandes et tapez `start inetmgr` pour ouvrir le composant logiciel enfichable MMC Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="6f873-123">Open a command prompt window and type `start inetmgr` to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2.  <span data-ttu-id="6f873-124">Dans le volet gauche, développez le nœud portant le nom d’ordinateur, puis le **Sites Web** nœud.</span><span class="sxs-lookup"><span data-stu-id="6f873-124">In the left pane, expand the node with the computer's name, and then expand the **Web Sites** node.</span></span>  
  
3.  <span data-ttu-id="6f873-125">Avec le bouton droit **Site Web par défaut** et sélectionnez **nouveau, le répertoire virtuel** pour ouvrir l’Assistant Création de répertoire virtuel.</span><span class="sxs-lookup"><span data-stu-id="6f873-125">Right-click **Default Web Site** and select **New, Virtual Directory** to open the Virtual Directory Creation wizard.</span></span>  
  
4.  <span data-ttu-id="6f873-126">Dans l’Assistant, tapez `servicemodelsamples` comme alias pour le répertoire virtuel que vous créez.</span><span class="sxs-lookup"><span data-stu-id="6f873-126">In the wizard, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5.  <span data-ttu-id="6f873-127">Affectez la valeur %SystemDrive%\inetpub\wwwroot\servicemodelsamples au chemin.</span><span class="sxs-lookup"><span data-stu-id="6f873-127">Set the path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span> <span data-ttu-id="6f873-128">La plupart des exemples [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] copient les fichiers exécutables de service dans cet emplacement une fois générés.</span><span class="sxs-lookup"><span data-stu-id="6f873-128">Most of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples copy service executable files to this location when built.</span></span>  
  
6.  <span data-ttu-id="6f873-129">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="6f873-129">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="6f873-130">Les cases à cocher suivantes sont activées par défaut :</span><span class="sxs-lookup"><span data-stu-id="6f873-130">By default, the following check boxes are selected:</span></span>  
  
    -   <span data-ttu-id="6f873-131">**En lecture**</span><span class="sxs-lookup"><span data-stu-id="6f873-131">**Read**</span></span>  
  
    -   <span data-ttu-id="6f873-132">**Exécuter des scripts (tels que ASP)**</span><span class="sxs-lookup"><span data-stu-id="6f873-132">**Run scripts (such as ASP)**</span></span>  
  
8.  <span data-ttu-id="6f873-133">Cliquez sur **suivant**, puis cliquez sur **Terminer** pour terminer l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="6f873-133">Click **Next**, and then click **Finish** to complete the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6f873-134">Cette tâche doit être exécutée une seule fois, car les exemples [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilisent tous le même répertoire virtuel (servicemodelsamples).</span><span class="sxs-lookup"><span data-stu-id="6f873-134">This task must be performed only once because all of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples use the same servicemodelsamples virtual directory.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a><span data-ttu-id="6f873-135">Pour définir les propriétés du répertoire virtuel supplémentaire dans IIS 7.0 ou 7.5</span><span class="sxs-lookup"><span data-stu-id="6f873-135">To set additional virtual directory properties in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="6f873-136">Cliquez sur le nœud servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="6f873-136">Click the servicemodelsamples node.</span></span> <span data-ttu-id="6f873-137">Deux vues figurent au bas de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="6f873-137">Along the bottom of the window, two views are listed.</span></span> <span data-ttu-id="6f873-138">Sélectionnez **affichage des fonctionnalités** s’il n’est pas déjà sélectionné.</span><span class="sxs-lookup"><span data-stu-id="6f873-138">Select **Features View** if it isn’t already selected.</span></span>  
  
2.  <span data-ttu-id="6f873-139">Double-cliquez sur l’entrée **exploration des répertoires**.</span><span class="sxs-lookup"><span data-stu-id="6f873-139">Double-click the entry for **Directory Browsing**.</span></span>  
  
3.  <span data-ttu-id="6f873-140">Dans le volet Actions, sélectionnez le **activer** option.</span><span class="sxs-lookup"><span data-stu-id="6f873-140">In the Actions pane, select the **Enable** option.</span></span> <span data-ttu-id="6f873-141">Cela permet d'accéder au répertoire du répertoire à l'aide d'Internet Explorer, ce qui est utile lors du débogage d'un service.</span><span class="sxs-lookup"><span data-stu-id="6f873-141">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
 <span data-ttu-id="6f873-142">Enfin, vous devez définir les propriétés de sécurité du dossier servicemodelsamples afin d'autoriser son accès.</span><span class="sxs-lookup"><span data-stu-id="6f873-142">Finally, you must set the security properties of the servicemodelsamples folder to allow it to be accessed by others.</span></span> <span data-ttu-id="6f873-143">Pour plus d'informations, consultez ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="6f873-143">See below for details.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a><span data-ttu-id="6f873-144">Pour définir des propriétés de répertoire virtuel supplémentaires dans IIS 5.1 ou 6.0</span><span class="sxs-lookup"><span data-stu-id="6f873-144">To set additional virtual directory properties in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="6f873-145">Cliquez sur le nœud servicemodelsamples, puis sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="6f873-145">Right-click the servicemodelsamples node and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="6f873-146">Les cases à cocher suivantes sont activées par défaut :</span><span class="sxs-lookup"><span data-stu-id="6f873-146">By default, the following check boxes are selected:</span></span>  
  
    -   <span data-ttu-id="6f873-147">**En lecture**</span><span class="sxs-lookup"><span data-stu-id="6f873-147">**Read**</span></span>  
  
    -   <span data-ttu-id="6f873-148">**Accès au journal**</span><span class="sxs-lookup"><span data-stu-id="6f873-148">**Log visits**</span></span>  
  
    -   <span data-ttu-id="6f873-149">**Indexer cette ressource**</span><span class="sxs-lookup"><span data-stu-id="6f873-149">**Index this resource**</span></span>  
  
3.  <span data-ttu-id="6f873-150">Sélectionnez le **exploration des répertoires** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="6f873-150">Select the **Directory browsing** check box.</span></span> <span data-ttu-id="6f873-151">Cela permet d'accéder au répertoire du répertoire à l'aide d'Internet Explorer, ce qui est utile lors du débogage d'un service.</span><span class="sxs-lookup"><span data-stu-id="6f873-151">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a><span data-ttu-id="6f873-152">Pour définir les propriétés de sécurité du dossier dans IIS 7.0 ou 7.5</span><span class="sxs-lookup"><span data-stu-id="6f873-152">To set security properties of the folder in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="6f873-153">Ouvrez le répertoire %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="6f873-153">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2.  <span data-ttu-id="6f873-154">Cliquez sur le dossier servicemodelsamples et cliquez sur **partage** ou **partager avec**.</span><span class="sxs-lookup"><span data-stu-id="6f873-154">Right-click the servicemodelsamples folder and click **Share** or **Share With**.</span></span>  
  
3.  <span data-ttu-id="6f873-155">Cliquez sur la flèche vers le bas à gauche de la **ajouter** bouton.</span><span class="sxs-lookup"><span data-stu-id="6f873-155">Click the down arrow to the left of the **Add** button.</span></span>  
  
4.  <span data-ttu-id="6f873-156">Sélectionnez le **trouver** entrée.</span><span class="sxs-lookup"><span data-stu-id="6f873-156">Select the **Find** entry.</span></span> <span data-ttu-id="6f873-157">Le **sélectionner des utilisateurs ou groupes** fenêtre s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="6f873-157">The **Select Users or Groups** window opens.</span></span>  
  
5.  <span data-ttu-id="6f873-158">Cliquez sur **Avancé**.</span><span class="sxs-lookup"><span data-stu-id="6f873-158">Click **Advanced**.</span></span>  
  
6.  <span data-ttu-id="6f873-159">Cliquez sur **emplacements**.</span><span class="sxs-lookup"><span data-stu-id="6f873-159">Click **Locations**.</span></span> <span data-ttu-id="6f873-160">Le **emplacements** fenêtre est maintenant ouverte.</span><span class="sxs-lookup"><span data-stu-id="6f873-160">The **Locations** window is now open.</span></span>  
  
7.  <span data-ttu-id="6f873-161">Sélectionnez l'entrée correspondant à l'ordinateur en cours d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="6f873-161">Select the entry for the computer being used.</span></span> <span data-ttu-id="6f873-162">Il est important de sélectionner l'ordinateur local et non une entrée correspondant à tous les domaines ou réseaux répertoriés.</span><span class="sxs-lookup"><span data-stu-id="6f873-162">It is important to select the local computer and not an entry for any domains or networks that are listed.</span></span> <span data-ttu-id="6f873-163">Après avoir sélectionné l’ordinateur, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6f873-163">After you have selected the computer, click **OK**.</span></span>  
  
8.  <span data-ttu-id="6f873-164">Cliquez sur **Rechercher maintenant**.</span><span class="sxs-lookup"><span data-stu-id="6f873-164">Click **Find Now**.</span></span> <span data-ttu-id="6f873-165">Cela permet d'inclure dans les résultats de la recherche les objets associés à l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="6f873-165">This populates the search results with objects associated with the local computer.</span></span>  
  
9. <span data-ttu-id="6f873-166">Rechercher les **IIS_IUSRS** entrée dans le **nom (nom unique relatif)** colonne.</span><span class="sxs-lookup"><span data-stu-id="6f873-166">Find the **IIS_IUSRS** entry in the **Name (Relative Distinguished Name)** column.</span></span> <span data-ttu-id="6f873-167">Sélectionnez cette entrée et cliquez sur **OK** pour la recherche de fermer la fenêtre Résultats.</span><span class="sxs-lookup"><span data-stu-id="6f873-167">Select that entry and click **OK** to close the search results window.</span></span>  
  
10. <span data-ttu-id="6f873-168">Cliquez sur **OK** pour fermer la **sélectionner des utilisateurs ou groupes** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="6f873-168">Click **OK** to close the **Select Users or Groups** window.</span></span>  
  
11. <span data-ttu-id="6f873-169">Cliquez sur **partage** pour conserver les modifications.</span><span class="sxs-lookup"><span data-stu-id="6f873-169">Click **Share** to persist the changes.</span></span>  
  
12. <span data-ttu-id="6f873-170">Une fois les modifications apportées à activer le partage, cliquez sur **fait** pour fermer la **le partage de fichiers** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="6f873-170">After the changes to enable sharing are complete, click **Done** to close the **File Sharing** window.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a><span data-ttu-id="6f873-171">Pour définir les propriétés de sécurité de ce dossier dans IIS 5.1 ou 6.0 :</span><span class="sxs-lookup"><span data-stu-id="6f873-171">To set security properties of the folder in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="6f873-172">Ouvrez le répertoire %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="6f873-172">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2.  <span data-ttu-id="6f873-173">Cliquez sur le **servicemodelsamples** dossier, puis cliquez sur **partage et sécurité.**</span><span class="sxs-lookup"><span data-stu-id="6f873-173">Right-click the **servicemodelsamples** folder and then click **Sharing and Security.**</span></span>  
  
3.  <span data-ttu-id="6f873-174">Cliquez sur l'onglet **Sécurité** .</span><span class="sxs-lookup"><span data-stu-id="6f873-174">Click the **Security** tab.</span></span>  
  
4.  <span data-ttu-id="6f873-175">Si vous utilisez IIS 6.0, dans le **noms d’utilisateur ou groupe** boîte, vérifiez si **compte Invité Internet** est répertorié.</span><span class="sxs-lookup"><span data-stu-id="6f873-175">If you are using IIS 6.0, in the **Group or user names** box, check whether **Internet Guest Account** is listed.</span></span>  
  
     <span data-ttu-id="6f873-176">Si ce n'est pas le cas :</span><span class="sxs-lookup"><span data-stu-id="6f873-176">If it is not listed:</span></span>  
  
    1.  <span data-ttu-id="6f873-177">Cliquez sur **Démarrer** puis cliquez sur **le panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="6f873-177">Click **Start** and then click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="6f873-178">Si vous ne voyez pas le **des comptes d’utilisateur** icône, cliquez sur **basculer vers l’affichage des catégories**.</span><span class="sxs-lookup"><span data-stu-id="6f873-178">If you do not see the **User Accounts** icon, click **Switch to Category View**.</span></span>  
  
    3.  <span data-ttu-id="6f873-179">Cliquez sur le **des comptes d’utilisateur** icône.</span><span class="sxs-lookup"><span data-stu-id="6f873-179">Click the **User Accounts** icon.</span></span>  
  
    4.  <span data-ttu-id="6f873-180">Sous « ou une icône du Panneau de configuration, » cliquez sur **des comptes d’utilisateur**.</span><span class="sxs-lookup"><span data-stu-id="6f873-180">Under "or pick a Control Panel icon," click **User Accounts**.</span></span>  
  
    5.  <span data-ttu-id="6f873-181">Dans le **des comptes d’utilisateur** boîte de dialogue, cliquez sur le **avancé** onglet.</span><span class="sxs-lookup"><span data-stu-id="6f873-181">In the **User Accounts** dialog box, click the **Advanced** tab.</span></span>  
  
    6.  <span data-ttu-id="6f873-182">Cliquez sur **Avancé**.</span><span class="sxs-lookup"><span data-stu-id="6f873-182">Click **Advanced**.</span></span>  
  
    7.  <span data-ttu-id="6f873-183">Dans le **utilisateurs et groupes locaux** boîte de dialogue, cliquez pour développer le **utilisateurs** dossier.</span><span class="sxs-lookup"><span data-stu-id="6f873-183">In the **Local Users and Groups** dialog box, click to expand the **Users** folder.</span></span>  
  
    8.  <span data-ttu-id="6f873-184">Dans le volet droit, double-cliquez sur **compte Invité Internet**.</span><span class="sxs-lookup"><span data-stu-id="6f873-184">In the right pane, double-click **Internet Guest Account**.</span></span>  
  
    9. <span data-ttu-id="6f873-185">Dans le **propriétés** boîte de dialogue, copiez le nom est utilisé en tant que compte Invité Internet.</span><span class="sxs-lookup"><span data-stu-id="6f873-185">In the **Properties** dialog box, copy the name used as the Internet guest account.</span></span> <span data-ttu-id="6f873-186">Par défaut, le nom commence par « USR_ » suivi du nom de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6f873-186">By default, the name begins with "USR_" followed by the name of the computer.</span></span>  
  
    10. <span data-ttu-id="6f873-187">Fermez la boîte de dialogue **Propriétés** .</span><span class="sxs-lookup"><span data-stu-id="6f873-187">Close the **Properties** dialog box.</span></span>  
  
    11. <span data-ttu-id="6f873-188">Fermer le **utilisateurs et groupes locaux** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6f873-188">Close the **Local Users and Groups** dialog box.</span></span>  
  
    12. <span data-ttu-id="6f873-189">Fermer le **des comptes d’utilisateur** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6f873-189">Close the **User Accounts** dialog box.</span></span>  
  
    13. <span data-ttu-id="6f873-190">Fermez l’autre **des comptes d’utilisateur** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6f873-190">Close the other **User Accounts** dialog box.</span></span>  
  
    14. <span data-ttu-id="6f873-191">Dans le **servicemodelsamples propriétés** boîte de dialogue le **sécurité** , cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="6f873-191">In the **servicemodelsamples Properties** dialog box, on the **Security** tab, click **Add**.</span></span>  
  
    15. <span data-ttu-id="6f873-192">Tapez le nom de l’ordinateur suivi d’une barre oblique inverse, puis collez le nom du compte d’utilisateur Internet, par exemple, myMachineName\\InternetGuestAccountName %</span><span class="sxs-lookup"><span data-stu-id="6f873-192">Type the name of the computer followed by a backslash, then paste the name of the Internet user account, for example, myMachineName\\%InternetGuestAccountName%</span></span>  
  
    16. <span data-ttu-id="6f873-193">Cliquez sur **vérifier les noms** pour vérifier l’ajout.</span><span class="sxs-lookup"><span data-stu-id="6f873-193">Click **Check Names** to verify the addition.</span></span> <span data-ttu-id="6f873-194">S'il est valide, ce nom figure en majuscules soulignées.</span><span class="sxs-lookup"><span data-stu-id="6f873-194">If it is valid, the name is in all capital letters and is underlined.</span></span>  
  
5.  <span data-ttu-id="6f873-195">Pour IIS 6.0, vérifiez également que le SERVICE réseau est répertorié dans le **noms d’utilisateur ou groupe** boîte.</span><span class="sxs-lookup"><span data-stu-id="6f873-195">For IIS 6.0, also check that NETWORK SERVICE is listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="6f873-196">Si SERVICE RÉSEAU n'est pas répertorié :</span><span class="sxs-lookup"><span data-stu-id="6f873-196">If NETWORK SERVICE is not listed:</span></span>  
  
    1.  <span data-ttu-id="6f873-197">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="6f873-197">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="6f873-198">Dans le **sélectionner des utilisateurs ou groupes** boîte de dialogue, tapez le nom de l’ordinateur suivi d’une barre oblique inverse.</span><span class="sxs-lookup"><span data-stu-id="6f873-198">In the **Select Users or Groups** dialog box, type the name of the computer followed by a backslash.</span></span>  
  
    3.  <span data-ttu-id="6f873-199">Type **service** après la barre oblique inverse (sans espace).</span><span class="sxs-lookup"><span data-stu-id="6f873-199">Type **service** after the backslash (no space).</span></span>  
  
    4.  <span data-ttu-id="6f873-200">Cliquez sur **vérifier les noms**.</span><span class="sxs-lookup"><span data-stu-id="6f873-200">Click **Check names**.</span></span>  
  
    5.  <span data-ttu-id="6f873-201">Si plusieurs noms sont trouvés, sélectionnez **SERVICE réseau** et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6f873-201">If multiple names are found, select **NETWORK SERVICE** and click **OK**.</span></span>  
  
    6.  <span data-ttu-id="6f873-202">Cliquez sur **OK** pour fermer la **sélectionner des utilisateurs ou groupes** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6f873-202">Click **OK** to close the **Select Users or Groups** dialog box.</span></span>  
  
6.  <span data-ttu-id="6f873-203">Si vous utilisez Windows XP SP2 avec IIS 5.1, vérifiez que le compte Invité Internet et ASPNET sont répertoriés dans le **noms d’utilisateur ou groupe** boîte.</span><span class="sxs-lookup"><span data-stu-id="6f873-203">If you are using Windows XP SP2 with IIS 5.1, check that both Internet Guest Account and ASPNET are listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="6f873-204">Notez que l’utilisateur ASPNET peut être un membre de la fonction intégrée **utilisateurs** groupe de sécurité.</span><span class="sxs-lookup"><span data-stu-id="6f873-204">Note that the ASPNET user may be a member of the built-in **Users** security group.</span></span> <span data-ttu-id="6f873-205">Dans ce cas, ensuite, si le **utilisateurs** groupe est répertorié dans la boîte de dialogue, vous n’avez pas besoin pour l’ajouter en tant qu’élément distinct à la liste des utilisateurs autorisés.</span><span class="sxs-lookup"><span data-stu-id="6f873-205">If so, then if the **Users** group is listed in the dialog box, you do not need to add it as a separate item to the list of permitted users.</span></span>  
  
     <span data-ttu-id="6f873-206">Pour vérifier qu’ASPNET fait partie de la **utilisateurs** groupe de sécurité :</span><span class="sxs-lookup"><span data-stu-id="6f873-206">To check if ASPNET is part of the **Users** security group:</span></span>  
  
    1.  <span data-ttu-id="6f873-207">Sur le **Démarrer** menu, cliquez sur **le panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="6f873-207">On the **Start** menu, click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="6f873-208">Cliquez sur le **des comptes d’utilisateur** icône.</span><span class="sxs-lookup"><span data-stu-id="6f873-208">Click the **User Accounts** icon.</span></span>  
  
    3.  <span data-ttu-id="6f873-209">Dans le **groupe** colonne, vérifiez que la valeur de **ASPNET** est « Utilisateurs ».</span><span class="sxs-lookup"><span data-stu-id="6f873-209">In the **Group** column, check that the value for **ASPNET** is "Users."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f873-210">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f873-210">See Also</span></span>  
 [<span data-ttu-id="6f873-211">Internet Information Service d’hébergement Instructions</span><span class="sxs-lookup"><span data-stu-id="6f873-211">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
