---
title: "Guide de déploiement du .NET Framework pour les administrateurs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
caps.latest.revision: 40
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 07b7381ddc94e3bc40a4eb0ed546f9526b57600a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="net-framework-deployment-guide-for-administrators"></a><span data-ttu-id="515f5-102">Guide de déploiement du .NET Framework pour les administrateurs</span><span class="sxs-lookup"><span data-stu-id="515f5-102">.NET Framework Deployment Guide for Administrators</span></span>
<span data-ttu-id="515f5-103">Cet article explique étape par étape comment un administrateur système peut déployer [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] et ses dépendances système dans un réseau à l'aide de Microsoft System Center Configuration Manager (SCCM).</span><span class="sxs-lookup"><span data-stu-id="515f5-103">This step-by-step article describes how a system administrator can deploy the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] and its system dependencies across a network by using Microsoft System Center Configuration Manager.</span></span> <span data-ttu-id="515f5-104">Cet article suppose que tous les ordinateurs clients cibles ont la configuration minimale requise pour le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="515f5-104">This article assumes that all target client computers meet the minimum requirements for the .NET Framework.</span></span> <span data-ttu-id="515f5-105">Pour obtenir la liste des configurations logicielle et matérielle requises pour installer le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], consultez [Configuration système requise](../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="515f5-105">For a list of the software and hardware requirements for installing the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], see [System Requirements](../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="515f5-106">Les logiciels référencés dans ce document, y compris, mais de manière non limitative, le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], System Center Configuration Manager et Active Directory, sont tous soumis à des termes et conditions de contrat de licence.</span><span class="sxs-lookup"><span data-stu-id="515f5-106">The software referenced in this document, including, without limitation, the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], System Center Configuration Manager, and Active Directory, are each subject to license terms and conditions.</span></span> <span data-ttu-id="515f5-107">Les présentes instructions supposent que lesdits termes et conditions du contrat de licence ont été passés en revue et acceptés par les propriétaires de licences des logiciels concernés.</span><span class="sxs-lookup"><span data-stu-id="515f5-107">These instructions assume that such license terms and conditions have been reviewed and accepted by the appropriate licensees of the software.</span></span> <span data-ttu-id="515f5-108">Ces instructions ne remplacent pas les termes et conditions desdits contrats de licence.</span><span class="sxs-lookup"><span data-stu-id="515f5-108">These instructions do not waive any of the terms and conditions of such license agreements.</span></span>  
>   
>  <span data-ttu-id="515f5-109">Pour plus d’informations sur la prise en charge du .NET Framework, consultez la [FAQ sur la politique de support pour Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=196607) sur le site web Aide et Support de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="515f5-109">For information about support for the .NET Framework, see [Microsoft .NET Framework Support Lifecycle Policy](http://go.microsoft.com/fwlink/?LinkId=196607) on the Microsoft Support website.</span></span>  
  
 <span data-ttu-id="515f5-110">Cette rubrique contient les sections suivantes :</span><span class="sxs-lookup"><span data-stu-id="515f5-110">This topic contains the following sections:</span></span>  
  
 <span data-ttu-id="515f5-111">[Processus de déploiement](#the_deployment_process) </span><span class="sxs-lookup"><span data-stu-id="515f5-111">[The deployment process](#the_deployment_process) </span></span>  
 <span data-ttu-id="515f5-112">[Déploiement du .NET Framework](#deploying_in_a_test_environment) </span><span class="sxs-lookup"><span data-stu-id="515f5-112">[Deploying the .NET Framework](#deploying_in_a_test_environment) </span></span>  
 [<span data-ttu-id="515f5-113">Créer un regroupement</span><span class="sxs-lookup"><span data-stu-id="515f5-113">Create a collection</span></span>](#creating_a_collection)  
 [<span data-ttu-id="515f5-114">Créer un package et un programme</span><span class="sxs-lookup"><span data-stu-id="515f5-114">Create a package and program</span></span>](#creating_a_package)  
 [<span data-ttu-id="515f5-115">Sélectionner un point de distribution</span><span class="sxs-lookup"><span data-stu-id="515f5-115">Select a distribution point</span></span>](#select_dist_point)  
 [<span data-ttu-id="515f5-116">Déployer le package</span><span class="sxs-lookup"><span data-stu-id="515f5-116">Deploy the package</span></span>](#deploying_package)  
[<span data-ttu-id="515f5-117">Ressources</span><span class="sxs-lookup"><span data-stu-id="515f5-117">Resources</span></span>](#resources)  
[<span data-ttu-id="515f5-118">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="515f5-118">Troubleshooting</span></span>](#troubleshooting)  
  
<a name="the_deployment_process"></a>   
## <a name="the-deployment-process"></a><span data-ttu-id="515f5-119">Processus de déploiement</span><span class="sxs-lookup"><span data-stu-id="515f5-119">The deployment process</span></span>  
 <span data-ttu-id="515f5-120">Lorsque l'infrastructure de prise en charge est en place, utilisez System Center 2012 Configuration Manager pour déployer le package redistribuable .Net Framework sur les ordinateurs du réseau.</span><span class="sxs-lookup"><span data-stu-id="515f5-120">When you have the supporting infrastructure in place, you use System Center 2012 Configuration Manager to deploy the .NET Framework redistributable package to computers on the network.</span></span> <span data-ttu-id="515f5-121">Générer l’infrastructure implique la création et la définition de cinq éléments principaux : les regroupements, un package et un programme pour les logiciels, des points de distribution et des déploiements.</span><span class="sxs-lookup"><span data-stu-id="515f5-121">Building the infrastructure involves creating and defining five primary areas: collections, a package and program for the software, distribution points, and deployments.</span></span>  
  
-   <span data-ttu-id="515f5-122">Les **regroupements** sont des ensembles de ressources de Configuration Manager, tels que des utilisateurs, des groupes d’utilisateurs ou des ordinateurs, sur lesquels le .Net Framework est déployé.</span><span class="sxs-lookup"><span data-stu-id="515f5-122">**Collections** are groups of Configuration Manager resources, such as users, user groups, or computers, to which the .NET Framework is deployed.</span></span> <span data-ttu-id="515f5-123">Pour plus d’informations, consultez [Regroupements dans Configuration Manager](http://technet.microsoft.com/library/gg682169.aspx) dans la bibliothèque de documentation Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="515f5-123">For more information, see [Collections in Configuration Manager](http://technet.microsoft.com/library/gg682169.aspx) in the Configuration Manager documentation library.</span></span>  
  
-   <span data-ttu-id="515f5-124">Les **packages et programmes** sont généralement les applications logicielles à installer sur un ordinateur client, mais ils peuvent également contenir des fichiers individuels, des mises à jour, ou même des commandes individuelles.</span><span class="sxs-lookup"><span data-stu-id="515f5-124">**Packages and programs** typically represent software applications to be installed on a client computer, but they might also contain individual files, updates, or even individual commands.</span></span> <span data-ttu-id="515f5-125">Pour plus d’informations, consultez [Packages et programmes dans Configuration Manager](http://technet.microsoft.com/library/gg699369.aspx) dans la bibliothèque de documentation Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="515f5-125">For more information, see [Packages and Programs in Configuration Manager](http://technet.microsoft.com/library/gg699369.aspx) in the Configuration Manager documentation library.</span></span>  
  
-   <span data-ttu-id="515f5-126">Les **points de distribution** sont des rôles de système de site Configuration Manager qui stockent les fichiers requis pour l’exécution des logiciels sur les ordinateurs clients.</span><span class="sxs-lookup"><span data-stu-id="515f5-126">**Distribution points** are Configuration Manager site system roles that store files required for software to run on client computers.</span></span> <span data-ttu-id="515f5-127">Lorsque le client Configuration Manager reçoit et traite un déploiement de logiciel, il contacte un point de distribution pour télécharger le contenu associé au logiciel et démarrer le processus d'installation.</span><span class="sxs-lookup"><span data-stu-id="515f5-127">When the Configuration Manager client receives and processes a software deployment, it contacts a distribution point to download the content associated with the software and to start the installation process.</span></span> <span data-ttu-id="515f5-128">Pour plus d’informations, consultez [Présentation de la gestion de contenu dans Configuration Manager](http://technet.microsoft.com/library/gg682083.aspx) dans la bibliothèque de documentation Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="515f5-128">For more information, see [Introduction to content Management in Configuration Manager](http://technet.microsoft.com/library/gg682083.aspx) in the Configuration Manager documentation library.</span></span>  
  
-   <span data-ttu-id="515f5-129">Les **déploiements** font en sorte que les membres applicables du regroupement cible spécifié installent le package logiciel.</span><span class="sxs-lookup"><span data-stu-id="515f5-129">**Deployments** instruct applicable members of the specified target collection to install the software package.</span></span> <span data-ttu-id="515f5-130">Pour plus d’informations, consultez [Comment déployer des applications dans Configuration Manager](http://technet.microsoft.com/library/gg682082.aspx) dans la bibliothèque de documentation Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="515f5-130">For more information, see [How to Deploy Applications in Configuration Manager](http://technet.microsoft.com/library/gg682082.aspx) in the Configuration Manager documentation library.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="515f5-131">Les procédures de cette rubrique contiennent les paramètres classiques pour créer et déployer un package et un programme, et ne couvrent pas tous les paramètres possibles.</span><span class="sxs-lookup"><span data-stu-id="515f5-131">The procedures in this topic contain typical settings for creating and deploying a package and program, and might not cover all possible settings.</span></span> <span data-ttu-id="515f5-132">Pour d’autres options de déploiement de Configuration Manager, consultez la [Bibliothèque de documentation Configuration Manager](http://technet.microsoft.com/library/gg682041.aspx).</span><span class="sxs-lookup"><span data-stu-id="515f5-132">For other Configuration Manager deployment options, see the [Configuration Manager Documentation Library](http://technet.microsoft.com/library/gg682041.aspx).</span></span>  
  
<a name="deploying_in_a_test_environment"></a>   
## <a name="deploying-the-net-framework"></a><span data-ttu-id="515f5-133">Déployer le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="515f5-133">Deploying the .NET Framework</span></span>  
 <span data-ttu-id="515f5-134">Vous pouvez utiliser System Center 2012 Configuration Manager pour déployer une installation sans assistance de [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], pour laquelle les utilisateurs n'interagissent pas avec le processus d'installation.</span><span class="sxs-lookup"><span data-stu-id="515f5-134">You can use System Center 2012 Configuration Manager to deploy a silent installation of the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], where the users do not interact with the installation process.</span></span> <span data-ttu-id="515f5-135">Procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="515f5-135">Follow these steps:</span></span>  
  
1.  <span data-ttu-id="515f5-136">[Créez un regroupement](#creating_a_collection).</span><span class="sxs-lookup"><span data-stu-id="515f5-136">[Create a collection](#creating_a_collection).</span></span>  
  
2.  <span data-ttu-id="515f5-137">[Créez un package et un programme pour le package redistribuable .Net Framework](#creating_a_package).</span><span class="sxs-lookup"><span data-stu-id="515f5-137">[Create a package and program for the .NET Framework redistributable](#creating_a_package).</span></span>  
  
3.  <span data-ttu-id="515f5-138">[Sélectionnez un point de distribution](#select_dist_point).</span><span class="sxs-lookup"><span data-stu-id="515f5-138">[Select a distribution point](#select_dist_point).</span></span>  
  
4.  <span data-ttu-id="515f5-139">[Déployez le package](#deploying_package).</span><span class="sxs-lookup"><span data-stu-id="515f5-139">[Deploy the package](#deploying_package).</span></span>  
  
<a name="creating_a_collection"></a>   
### <a name="create-a-collection"></a><span data-ttu-id="515f5-140">Créer un regroupement</span><span class="sxs-lookup"><span data-stu-id="515f5-140">Create a collection</span></span>  
 <span data-ttu-id="515f5-141">Dans cette étape, sélectionnez les ordinateurs sur lesquels seront déployés le package et le programme, et regroupez-les dans un regroupement de périphériques.</span><span class="sxs-lookup"><span data-stu-id="515f5-141">In this step, you select the computers to which you will deploy the package and program, and group them into a device collection.</span></span> <span data-ttu-id="515f5-142">Pour créer un regroupement dans Configuration Manager, utilisez des règles d’adhésion directes (où les membres du regroupement sont spécifiés manuellement) ou des règles de requête (où Configuration Manager détermine les membres du regroupement selon des critères que vous avez spécifiés).</span><span class="sxs-lookup"><span data-stu-id="515f5-142">To create a collection in Configuration Manager, you can use direct membership rules (where you manually specify the collection members) or query rules (where Configuration Manager determines the collection members based on criteria you specify).</span></span> <span data-ttu-id="515f5-143">Pour plus d’informations sur les règles d’adhésion, notamment les règles directes et de requête, consultez [Introduction aux regroupements dans Configuration Manager](http://technet.microsoft.com/library/gg682177.aspx) dans la bibliothèque de documentation Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="515f5-143">For more information about membership rules, including queries and direct rules, see [Introduction to Collections in Configuration Manager](http://technet.microsoft.com/library/gg682177.aspx) in the Configuration Manager Documentation Library.</span></span>  
  
 <span data-ttu-id="515f5-144">Pour créer un regroupement</span><span class="sxs-lookup"><span data-stu-id="515f5-144">To create a collection:</span></span>  
  
1.  <span data-ttu-id="515f5-145">Dans la Console Configuration Manager, choisissez **Ressources et Conformité**.</span><span class="sxs-lookup"><span data-stu-id="515f5-145">In the Configuration Manager console, choose **Assets and Compliance**.</span></span>  
  
2.  <span data-ttu-id="515f5-146">Dans l’espace de travail **Ressources et Conformité**, choisissez **Regroupements de périphériques**.</span><span class="sxs-lookup"><span data-stu-id="515f5-146">In the **Assets and Compliance** workspace, choose **Device Collections**.</span></span>  
  
3.  <span data-ttu-id="515f5-147">Sous l’onglet **Accueil** dans le groupe **Créer**, choisissez **Créer un regroupement de périphériques**.</span><span class="sxs-lookup"><span data-stu-id="515f5-147">On the **Home** tab in the **Create** group, choose **Create Device Collection**.</span></span>  
  
4.  <span data-ttu-id="515f5-148">Dans la page **Général** de l’**Assistant Création d’un regroupement de périphériques**, entrez un nom pour le regroupement.</span><span class="sxs-lookup"><span data-stu-id="515f5-148">On the **General** page of the **Create Device Collection Wizard**, enter a name for the collection.</span></span>  
  
5.  <span data-ttu-id="515f5-149">Choisissez **Parcourir** pour spécifier un regroupement limité.</span><span class="sxs-lookup"><span data-stu-id="515f5-149">Choose **Browse** to specify a limiting collection.</span></span>  
  
6.  <span data-ttu-id="515f5-150">Dans la page **Règles d’adhésion**, choisissez **Ajouter une règle**, puis **Règle directe** pour ouvrir l’**Assistant Création d’une règle d’adhésion directe**.</span><span class="sxs-lookup"><span data-stu-id="515f5-150">On the **Membership Rules** page, choose **Add Rule**, and then choose **Direct Rule** to open the **Create Direct Membership Rule Wizard**.</span></span> <span data-ttu-id="515f5-151">Sélectionnez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="515f5-151">Choose **Next**.</span></span>  
  
7.  <span data-ttu-id="515f5-152">Dans la page **Rechercher des ressources**, dans la liste **Classe de ressource**, choisissez **Ressource système**.</span><span class="sxs-lookup"><span data-stu-id="515f5-152">On the **Search for Resources** page, in the **Resource class** list, choose **System Resource**.</span></span> <span data-ttu-id="515f5-153">Dans la liste **Nom de l’attribut**, choisissez **Nom**.</span><span class="sxs-lookup"><span data-stu-id="515f5-153">In the **Attribute name** list, choose **Name**.</span></span> <span data-ttu-id="515f5-154">Dans le champ **Valeur**, entrez `%` et choisissez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="515f5-154">In the **Value** field, enter `%`, and then choose **Next**.</span></span>  
  
8.  <span data-ttu-id="515f5-155">Dans la page **Sélectionner les ressources**, cochez la case de chaque ordinateur sur lequel vous souhaitez déployer le .Net Framework.</span><span class="sxs-lookup"><span data-stu-id="515f5-155">On the **Select Resources** page, select the check box for each computer that you want to deploy the .NET Framework to.</span></span> <span data-ttu-id="515f5-156">Choisissez **Suivant**, puis terminez l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="515f5-156">Choose **Next**, and then complete the wizard.</span></span>  
  
9. <span data-ttu-id="515f5-157">Dans la page **Règles d’adhésion** de l’**Assistant Création d’un regroupement de périphériques**, choisissez **Suivant**, puis terminez l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="515f5-157">On the **Membership Rules** page of the **Create Device Collection Wizard**, choose **Next**, and then complete the wizard.</span></span>  
  
 <span data-ttu-id="515f5-158">Pour plus d’informations sur les regroupements, consultez [Regroupements dans Configuration Manager](http://technet.microsoft.com/library/bb693730.aspx) dans la bibliothèque de documentation Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="515f5-158">For more information about collections, see [Collections in Configuration Manager](http://technet.microsoft.com/library/bb693730.aspx) in the Configuration Manager Documentation Library.</span></span>  
  
<a name="creating_a_package"></a>   
### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a><span data-ttu-id="515f5-159">Créer un package et un programme pour le package redistribuable .Net Framework</span><span class="sxs-lookup"><span data-stu-id="515f5-159">Create a package and program for the .NET Framework redistributable package</span></span>  
 <span data-ttu-id="515f5-160">Les étapes suivantes permettent de créer manuellement un package pour le package redistribuable .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="515f5-160">The following steps create a package for the .NET Framework redistributable manually.</span></span> <span data-ttu-id="515f5-161">Le package contient les paramètres spécifiés pour l'installation du .Net Framework et l'emplacement à partir duquel le package sera distribué aux ordinateurs cibles.</span><span class="sxs-lookup"><span data-stu-id="515f5-161">The package contains the specified parameters for installing the .NET Framework and the location from where the package will be distributed to the target computers.</span></span>  
  
 <span data-ttu-id="515f5-162">Pour créer un package :</span><span class="sxs-lookup"><span data-stu-id="515f5-162">To create a package:</span></span>  
  
1.  <span data-ttu-id="515f5-163">Dans la Console Configuration Manager, choisissez **Bibliothèque de logiciels**.</span><span class="sxs-lookup"><span data-stu-id="515f5-163">In the Configuration Manager console, choose **Software Library**..</span></span>  
  
2.  <span data-ttu-id="515f5-164">Dans l’espace de travail **Bibliothèque de logiciels**, développez **Gestion des applications**, puis choisissez **Packages**.</span><span class="sxs-lookup"><span data-stu-id="515f5-164">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>  
  
3.  <span data-ttu-id="515f5-165">Sous l’onglet **Accueil**, dans le groupe **Créer**, choisissez **Créer un package**.</span><span class="sxs-lookup"><span data-stu-id="515f5-165">On the **Home** tab, in the **Create** group, choose **Create Package**.</span></span>  
  
4.  <span data-ttu-id="515f5-166">Dans la page **Package** de l’**Assistant Création d’un package et d’un programme**, entrez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="515f5-166">On the **Package** page of the **Create Package and Program Wizard**, enter the following information:</span></span>  
  
    -   <span data-ttu-id="515f5-167">Nom : `.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="515f5-167">Name: `.NET Framework 4.5`</span></span>  
  
    -   <span data-ttu-id="515f5-168">Fabricant : `Microsoft`</span><span class="sxs-lookup"><span data-stu-id="515f5-168">Manufacturer: `Microsoft`</span></span>  
  
    -   <span data-ttu-id="515f5-169">Langue :</span><span class="sxs-lookup"><span data-stu-id="515f5-169">Language.</span></span> `English (US)`  
  
5.  <span data-ttu-id="515f5-170">Choisissez **Ce package contient des fichiers sources**, puis **Parcourir** pour sélectionner le dossier local ou réseau qui contient les fichiers d’installation du .Net Framework.</span><span class="sxs-lookup"><span data-stu-id="515f5-170">Choose **This package contains source files**, and then choose **Browse** to select the local or network folder that contains the .NET Framework installation files.</span></span> <span data-ttu-id="515f5-171">Quand vous avez sélectionné le dossier, choisissez **OK**, puis **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="515f5-171">When you have selected the folder, choose **OK**, and then choose **Next**.</span></span>  
  
6.  <span data-ttu-id="515f5-172">Dans la page **Type de programme** de l’Assistant, choisissez **Programme standard**, puis **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="515f5-172">On the **Program Type** page of the wizard, choose **Standard Program**, and then choose **Next**.</span></span>  
  
7.  <span data-ttu-id="515f5-173">Dans la page **Programme** de l’**Assistant Création d’un package et d’un programme**, entrez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="515f5-173">On the **Program** page of the **Create Package and Program Wizard**, enter the following information:</span></span>  
  
    1.  <span data-ttu-id="515f5-174">**Nom :** `.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="515f5-174">**Name:** `.NET Framework 4.5`</span></span>  
  
    2.  <span data-ttu-id="515f5-175">**Ligne de commande :** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (les options de ligne de commande sont décrites dans le tableau après ces étapes)</span><span class="sxs-lookup"><span data-stu-id="515f5-175">**Command line:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (command-line options are described in the table after these steps)</span></span>  
  
    3.  <span data-ttu-id="515f5-176">**Exécuter :** choisissez **Masqué**.</span><span class="sxs-lookup"><span data-stu-id="515f5-176">**Run:** Choose **Hidden**.</span></span>  
  
    4.  <span data-ttu-id="515f5-177">**Le programme peut s’exécuter :** sélectionnez l’option qui spécifie que le programme peut s’exécuter que l’utilisateur soit connecté ou non.</span><span class="sxs-lookup"><span data-stu-id="515f5-177">**Program can run:** Choose the option that specifies that the program can run regardless of whether a user is logged on.</span></span>  
  
8.  <span data-ttu-id="515f5-178">Dans la page **Exigences**, acceptez les valeurs par défaut en choisissant **Suivant**, puis terminez l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="515f5-178">On the **Requirements** page, choose **Next** to accept the default values, and then complete the wizard.</span></span>  
  
 <span data-ttu-id="515f5-179">Le tableau suivant décrit les options de ligne de commande spécifiées dans l'étape 7.</span><span class="sxs-lookup"><span data-stu-id="515f5-179">The following table describes the command-line options specified in step 7.</span></span>  
  
|<span data-ttu-id="515f5-180">Option</span><span class="sxs-lookup"><span data-stu-id="515f5-180">Option</span></span>|<span data-ttu-id="515f5-181">Description</span><span class="sxs-lookup"><span data-stu-id="515f5-181">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="515f5-182">**/q**</span><span class="sxs-lookup"><span data-stu-id="515f5-182">**/q**</span></span>|<span data-ttu-id="515f5-183">Définit le mode silencieux.</span><span class="sxs-lookup"><span data-stu-id="515f5-183">Sets quiet mode.</span></span> <span data-ttu-id="515f5-184">Aucune entrée d'utilisateur n'est requise, et aucun résultat n'est affiché.</span><span class="sxs-lookup"><span data-stu-id="515f5-184">No user input is required, and no output is shown.</span></span>|  
|<span data-ttu-id="515f5-185">**/norestart**</span><span class="sxs-lookup"><span data-stu-id="515f5-185">**/norestart**</span></span>|<span data-ttu-id="515f5-186">Empêche le programme d'installation de redémarrer automatiquement.</span><span class="sxs-lookup"><span data-stu-id="515f5-186">Prevents the Setup program from rebooting automatically.</span></span> <span data-ttu-id="515f5-187">Si vous utilisez cette option, Configuration Manager doit gérer le redémarrage de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="515f5-187">If you use this option, Configuration Manager must handle the computer restart.</span></span>|  
|<span data-ttu-id="515f5-188">**/chainingpackage** *nom_package*</span><span class="sxs-lookup"><span data-stu-id="515f5-188">**/chainingpackage** *PackageName*</span></span>|<span data-ttu-id="515f5-189">Spécifie le nom du package qui effectue le chaînage.</span><span class="sxs-lookup"><span data-stu-id="515f5-189">Specifies the name of the package that is doing the chaining.</span></span> <span data-ttu-id="515f5-190">Ces informations sont stockées avec d’autres informations de session d’installation pour les personnes inscrites au [Programme d’amélioration du produit Microsoft (CEIP)](http://go.microsoft.com/fwlink/p/?LinkId=248244).</span><span class="sxs-lookup"><span data-stu-id="515f5-190">This information is reported with other installation session information for those who have signed up for the [Microsoft Customer Experience Improvement Program (CEIP)](http://go.microsoft.com/fwlink/p/?LinkId=248244).</span></span> <span data-ttu-id="515f5-191">Si le nom du package inclut des espaces, utilisez des guillemets doubles comme délimiteurs. Par exemple : **/chainingpackage "Chaining Product"**.</span><span class="sxs-lookup"><span data-stu-id="515f5-191">If the package name includes spaces, use double quotation marks as delimiters; for example: **/chainingpackage "Chaining Product"**.</span></span>|  
  
 <span data-ttu-id="515f5-192">Les étapes suivantes créent un package nommé .Net Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="515f5-192">These steps create a package named .NET Framework 4.5.</span></span> <span data-ttu-id="515f5-193">Le programme déploie une installation sans assistance de .Net Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="515f5-193">The program deploys a silent installation of the .NET Framework 4.5.</span></span> <span data-ttu-id="515f5-194">Dans une installation sans assistance, les utilisateurs n’interagissent pas avec le processus d’installation et l’application de chaînage doit capturer le code de retour et gérer le redémarrage. Voir [Getting Progress Information from an Installation Package (Obtention d’informations de progression d’un package d’installation)](http://go.microsoft.com/fwlink/?LinkId=179606) dans MSDN Library.</span><span class="sxs-lookup"><span data-stu-id="515f5-194">In a silent installation, users do not interact with the installation process, and the chaining application has to capture the return code and handle rebooting; see [Getting Progress Information from an Installation Package](http://go.microsoft.com/fwlink/?LinkId=179606) in the MSDN Library.</span></span>  
  
<a name="select_dist_point"></a>   
### <a name="select-a-distribution-point"></a><span data-ttu-id="515f5-195">Sélectionner un point de distribution</span><span class="sxs-lookup"><span data-stu-id="515f5-195">Select a distribution point</span></span>  
 <span data-ttu-id="515f5-196">Pour distribuer le package et le programme aux ordinateurs clients à partir d'un serveur, vous devez d'abord désigner un système de site comme un point de distribution, puis distribuer le package au point de distribution.</span><span class="sxs-lookup"><span data-stu-id="515f5-196">To distribute the package and program to client computers from a server, you must first designate a site system as a distribution point and then distribute the package to the distribution point.</span></span>  
  
 <span data-ttu-id="515f5-197">Utilisez les étapes suivantes pour sélectionner un point de distribution pour le package de .Net Framework 4.5 créé au cours la section précédente :</span><span class="sxs-lookup"><span data-stu-id="515f5-197">Use the following steps to select a distribution point for the .NET Framework 4.5 package you created in the previous section:</span></span>  
  
1.  <span data-ttu-id="515f5-198">Dans la Console Configuration Manager, choisissez **Bibliothèque de logiciels**.</span><span class="sxs-lookup"><span data-stu-id="515f5-198">In the Configuration Manager console, choose **Software Library**.</span></span>  
  
2.  <span data-ttu-id="515f5-199">Dans l’espace de travail **Bibliothèque de logiciels**, développez **Gestion des applications**, puis choisissez **Packages**.</span><span class="sxs-lookup"><span data-stu-id="515f5-199">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>  
  
3.  <span data-ttu-id="515f5-200">Dans la liste de packages, sélectionnez le package **.Net Framework 4.5** créé dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="515f5-200">From the list of packages, select the package **.NET Framework 4.5** that you created in the previous section.</span></span>  
  
4.  <span data-ttu-id="515f5-201">Sous l’onglet **Accueil**, dans le groupe **Déploiement**, choisissez **Distribuer du contenu**.</span><span class="sxs-lookup"><span data-stu-id="515f5-201">On the **Home** tab, in the **Deployment** group, choose **Distribute Content**.</span></span>  
  
5.  <span data-ttu-id="515f5-202">Sous l’onglet **Général** de l’**Assistant Distribuer du contenu**, choisissez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="515f5-202">On the **General** tab of the **Distribute Content Wizard**, choose **Next**.</span></span>  
  
6.  <span data-ttu-id="515f5-203">Dans la page **Destination du contenu** de l’Assistant, choisissez **Ajouter**, puis **Point de distribution**.</span><span class="sxs-lookup"><span data-stu-id="515f5-203">On the **Content Destination** page of the wizard, choose **Add**, and then choose **Distribution Point**.</span></span>  
  
7.  <span data-ttu-id="515f5-204">Dans la boîte de dialogue **Ajouter des points de distribution**, sélectionnez les points de distribution qui hébergeront le package et le programme, puis choisissez **OK**.</span><span class="sxs-lookup"><span data-stu-id="515f5-204">In the **Add Distribution Points** dialog box, select the distribution point(s) that will host the package and program, and then choose **OK**.</span></span>  
  
8.  <span data-ttu-id="515f5-205">Effectuez toutes les étapes de l'Assistant.</span><span class="sxs-lookup"><span data-stu-id="515f5-205">Complete the wizard.</span></span>  
  
 <span data-ttu-id="515f5-206">Le package contient désormais toutes les informations nécessaires au déploiement sans assistance du .Net Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="515f5-206">The packagenow contains all the information you need to silently deploy the .NET Framework 4.5.</span></span> <span data-ttu-id="515f5-207">Avant de déployer le package et le programme, vérifiez qu’il a été installé sur le point de distribution ; consultez la section « Surveiller le contenu » de la page [Opérations et maintenance de la gestion de contenu dans Configuration Manager](http://technet.microsoft.com/library/gg712694.aspx#BKMK_MonitorContent) dans la bibliothèque de la documentation Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="515f5-207">Before you deploy the package and program, verify that it was installed on the distribution point; see the "Monitor Content" section of [Operations and Maintenance for Content Management in Configuration Manager](http://technet.microsoft.com/library/gg712694.aspx#BKMK_MonitorContent) in the Configuration Manager Documentation Library.</span></span>  
  
<a name="deploying_package"></a>   
### <a name="deploy-the-package"></a><span data-ttu-id="515f5-208">Déployer le package</span><span class="sxs-lookup"><span data-stu-id="515f5-208">Deploy the package</span></span>  
 <span data-ttu-id="515f5-209">Pour déployer le package et le programme .Net Framework 4.5 :</span><span class="sxs-lookup"><span data-stu-id="515f5-209">To deploy the .NET Framework 4.5 package and program:</span></span>  
  
1.  <span data-ttu-id="515f5-210">Dans la Console Configuration Manager, choisissez **Bibliothèque de logiciels**.</span><span class="sxs-lookup"><span data-stu-id="515f5-210">In the Configuration Manager console, choose **Software Library**.</span></span>  
  
2.  <span data-ttu-id="515f5-211">Dans l’espace de travail **Bibliothèque de logiciels**, développez **Gestion des applications**, puis choisissez **Packages**.</span><span class="sxs-lookup"><span data-stu-id="515f5-211">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>  
  
3.  <span data-ttu-id="515f5-212">Dans la liste des packages, sélectionnez le package que vous avez créé, appelé **.Net Framework 4.5**.</span><span class="sxs-lookup"><span data-stu-id="515f5-212">From the list of packages, select the package you created named **.NET Framework 4.5**.</span></span>  
  
4.  <span data-ttu-id="515f5-213">Sous l’onglet **Accueil**, dans le groupe **Déploiement**, choisissez **Déployer**.</span><span class="sxs-lookup"><span data-stu-id="515f5-213">On the **Home** tab, in the **Deployment** group, choose **Deploy**.</span></span>  
  
5.  <span data-ttu-id="515f5-214">Dans la page **Général** de l’**Assistant Déploiement logiciel**, choisissez **Parcourir**, puis sélectionnez le regroupement créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="515f5-214">On the **General** page of the **Deploy Software Wizard**, choose **Browse**, and then select the collection that you created earlier.</span></span> <span data-ttu-id="515f5-215">Sélectionnez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="515f5-215">Choose **Next**.</span></span>  
  
6.  <span data-ttu-id="515f5-216">Dans la page **Contenu** de l’Assistant, vérifiez que le point à partir duquel vous souhaitez distribuer le logiciel s’affiche, puis choisissez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="515f5-216">On the **Content** page of the wizard, verify that the point from which you want to distribute the software is displayed, and then choose **Next**.</span></span>  
  
7.  <span data-ttu-id="515f5-217">Dans la page **Paramètres de déploiement** de l’Assistant, vérifiez que **Action** est défini sur **Installer**, et **Objectif** sur **Requis**.</span><span class="sxs-lookup"><span data-stu-id="515f5-217">On the **Deployment Settings** page of the wizard, confirm that **Action** is set to **Install**, and **Purpose** is set to **Required**.</span></span> <span data-ttu-id="515f5-218">Cela garantit que le package logiciel est une installation obligatoire sur les ordinateurs ciblés.</span><span class="sxs-lookup"><span data-stu-id="515f5-218">This ensures that the software package will be a mandatory installation on the targeted computers.</span></span> <span data-ttu-id="515f5-219">Sélectionnez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="515f5-219">Choose **Next**.</span></span>  
  
8.  <span data-ttu-id="515f5-220">Dans la page **Planification** de l’Assistant, spécifiez à quel moment vous souhaitez que le .Net Framework soit installé.</span><span class="sxs-lookup"><span data-stu-id="515f5-220">On the **Scheduling** page of the wizard, specify when you want the .NET Framework to be installed.</span></span> <span data-ttu-id="515f5-221">Choisissez **Nouveau** pour déterminer le moment de l’installation, ou demandez au logiciel d’effectuer l’installation quand l’utilisateur se connecte ou se déconnecte, ou dès que possible.</span><span class="sxs-lookup"><span data-stu-id="515f5-221">You can choose **New** to assign an installation time, or instruct the software to install when the user logs on or off, or as soon as possible.</span></span> <span data-ttu-id="515f5-222">Sélectionnez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="515f5-222">Choose **Next**.</span></span>  
  
9. <span data-ttu-id="515f5-223">Dans la page **Expérience utilisateur** de l’Assistant, utilisez les valeurs par défaut et choisissez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="515f5-223">On the **User Experience** page of the wizard, use the default values and choose **Next**.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="515f5-224">Il est possible que votre environnement de production ait des stratégies qui requièrent des sélections différentes pour la planification de déploiement.</span><span class="sxs-lookup"><span data-stu-id="515f5-224">Your production environment might have policies that require different selections for the deployment schedule.</span></span> <span data-ttu-id="515f5-225">Pour plus d’informations sur ces options, consultez [Propriétés du nom de la publication : Onglet Calendrier](http://technet.microsoft.com/library/bb694016.aspx) dans la bibliothèque TechNet.</span><span class="sxs-lookup"><span data-stu-id="515f5-225">For information about these options, see [Advertisement Name Properties: Schedule Tab](http://technet.microsoft.com/library/bb694016.aspx) in the TechNet Library.</span></span>  
  
10. <span data-ttu-id="515f5-226">Dans la page **Points de distribution** de l’Assistant, utilisez les valeurs par défaut et choisissez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="515f5-226">On the **Distribution Points** page of the wizard, use the default values and choose **Next**.</span></span>  
  
11. <span data-ttu-id="515f5-227">Effectuez toutes les étapes de l'Assistant.</span><span class="sxs-lookup"><span data-stu-id="515f5-227">Complete the wizard.</span></span> <span data-ttu-id="515f5-228">Vous pouvez surveiller la progression du déploiement dans le nœud **Déploiements** de l’espace de travail **Surveillance**.</span><span class="sxs-lookup"><span data-stu-id="515f5-228">You can monitor the progress of the deployment in the **Deployments** node of the **Monitoring** workspace.</span></span>  
  
 <span data-ttu-id="515f5-229">Le package est déployé dans le regroupement ciblé et l’installation sans assistance du .Net Framework 4.5 peut commencer.</span><span class="sxs-lookup"><span data-stu-id="515f5-229">The package will now be deployed to the targeted collection and the silent installation of .NET Framework 4.5 will begin.</span></span> <span data-ttu-id="515f5-230">Pour plus d’informations sur les codes d’erreur liés à l’installation du .NET Framework 4.5, consultez la section [Codes de retour](#return_codes) plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="515f5-230">For information about .NET Framework 4.5 installation error codes, see the [Return Codes](#return_codes) section later in this topic.</span></span>  
  
<a name="resources"></a>   
## <a name="resources"></a><span data-ttu-id="515f5-231">Ressources</span><span class="sxs-lookup"><span data-stu-id="515f5-231">Resources</span></span>  
 <span data-ttu-id="515f5-232">Pour plus d'informations sur l'infrastructure pour tester le déploiement du package redistribuable [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], consultez les ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="515f5-232">For more information about the infrastructure for testing the deployment of the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable package, see the following resources.</span></span>  
  
 <span data-ttu-id="515f5-233">**Active Directory, DNS, DHCP :**</span><span class="sxs-lookup"><span data-stu-id="515f5-233">**Active Directory, DNS, DHCP:**</span></span>  
  
-   [<span data-ttu-id="515f5-234">Services de domaine Active Directory pour Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="515f5-234">Active Directory Domain Services for Windows Server 2008</span></span>](http://technet.microsoft.com/library/dd378891.aspx)  
  
-   [<span data-ttu-id="515f5-235">Serveur DNS</span><span class="sxs-lookup"><span data-stu-id="515f5-235">DNS Server</span></span>](http://technet.microsoft.com/library/cc732997.aspx)  
  
-   [<span data-ttu-id="515f5-236">Serveur DHCP</span><span class="sxs-lookup"><span data-stu-id="515f5-236">DHCP Server</span></span>](http://technet.microsoft.com/library/cc896553.aspx)  
  
 <span data-ttu-id="515f5-237">**SQL Server 2008 :**</span><span class="sxs-lookup"><span data-stu-id="515f5-237">**SQL Server 2008:**</span></span>  
  
-   [<span data-ttu-id="515f5-238">Installation de SQL Server 2008 (Vidéo liée à SQL Server)</span><span class="sxs-lookup"><span data-stu-id="515f5-238">Installing SQL Server 2008 (SQL Server Video)</span></span>](http://technet.microsoft.com/library/dd299415.aspx)  
  
-   [<span data-ttu-id="515f5-239">Présentation de la sécurité SQL Server 2008 pour les administrateurs de base de données</span><span class="sxs-lookup"><span data-stu-id="515f5-239">SQL Server 2008 Security Overview for Database Administrators</span></span>](http://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)  
  
 <span data-ttu-id="515f5-240">**System Center 2012 Configuration Manager (point de gestion, point de distribution) :**</span><span class="sxs-lookup"><span data-stu-id="515f5-240">**System Center 2012 Configuration Manager (Management Point, Distribution Point):**</span></span>  
  
-   [<span data-ttu-id="515f5-241">Administration de site pour System Center 2012 Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="515f5-241">Site Administration for System Center 2012 Configuration Manager</span></span>](http://technet.microsoft.com/library/gg681983.aspx)  
  
-   [<span data-ttu-id="515f5-242">Planification et déploiement d’un site Configuration Manager unique</span><span class="sxs-lookup"><span data-stu-id="515f5-242">Configuration Manager Single Site Planning and Deployment</span></span>](http://technet.microsoft.com/library/bb680961.aspx)  
  
 <span data-ttu-id="515f5-243">**Client System Center 2012 Configuration Manager pour des ordinateurs Windows :**</span><span class="sxs-lookup"><span data-stu-id="515f5-243">**System Center 2012 Configuration Manager client for Windows computers:**</span></span>  
  
-   [<span data-ttu-id="515f5-244">Déploiement de clients pour System Center 2012 Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="515f5-244">Deploying Clients for System Center 2012 Configuration Manager</span></span>](http://technet.microsoft.com/library/gg699391.aspx)  
  
<a name="troubleshooting"></a>   
## <a name="troubleshooting"></a><span data-ttu-id="515f5-245">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="515f5-245">Troubleshooting</span></span>  
  
### <a name="log-file-locations"></a><span data-ttu-id="515f5-246">Emplacements des fichiers journaux</span><span class="sxs-lookup"><span data-stu-id="515f5-246">Log file locations</span></span>  
 <span data-ttu-id="515f5-247">Les fichiers journaux suivants sont générés pendant l'installation du [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="515f5-247">The following log files are generated during [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup:</span></span>  
  
 <span data-ttu-id="515f5-248">%temp%\Microsoft .NET Framework 4.5*.txt</span><span class="sxs-lookup"><span data-stu-id="515f5-248">%temp%\Microsoft .NET Framework 4.5*.txt</span></span>   
 <span data-ttu-id="515f5-249">%temp%\Microsoft .NET Framework 4.5\*.html</span><span class="sxs-lookup"><span data-stu-id="515f5-249">%temp%\Microsoft .NET Framework 4.5\*.html</span></span>  
  
 <span data-ttu-id="515f5-250">Vous pouvez utiliser l’[outil de collecte des journaux](http://www.microsoft.com/download/details.aspx?id=12493) pour collecter les fichiers journaux [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] et créer un fichier CAB compressé (.cab) afin de réduire la taille des fichiers.</span><span class="sxs-lookup"><span data-stu-id="515f5-250">You can use the [log collection tool](http://www.microsoft.com/download/details.aspx?id=12493) to collect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] log files and to create a compressed cabinet (.cab) file that reduces the size of the files.</span></span>  
  
<a name="return_codes"></a>   
### <a name="return-codes"></a><span data-ttu-id="515f5-251">Codes de retour</span><span class="sxs-lookup"><span data-stu-id="515f5-251">Return codes</span></span>  
 <span data-ttu-id="515f5-252">Le tableau suivant répertorie les codes de retour les plus courants pour le programme d'installation du package redistribuable [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="515f5-252">The following table lists the most common return codes from the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable installation program.</span></span> <span data-ttu-id="515f5-253">Les codes de retour sont identiques pour toutes les versions du programme d'installation.</span><span class="sxs-lookup"><span data-stu-id="515f5-253">The return codes are the same for all versions of the installer.</span></span>  
  
 <span data-ttu-id="515f5-254">Pour plus d’informations, consultez la section suivante : [Codes d’erreur de téléchargement](#additional_error_codes).</span><span class="sxs-lookup"><span data-stu-id="515f5-254">For links to detailed information, see the next section, [Download error codes](#additional_error_codes).</span></span>  
  
|<span data-ttu-id="515f5-255">Code de retour</span><span class="sxs-lookup"><span data-stu-id="515f5-255">Return code</span></span>|<span data-ttu-id="515f5-256">Description</span><span class="sxs-lookup"><span data-stu-id="515f5-256">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="515f5-257">0</span><span class="sxs-lookup"><span data-stu-id="515f5-257">0</span></span>|<span data-ttu-id="515f5-258">Installation terminée.</span><span class="sxs-lookup"><span data-stu-id="515f5-258">Installation completed successfully.</span></span>|  
|<span data-ttu-id="515f5-259">1602</span><span class="sxs-lookup"><span data-stu-id="515f5-259">1602</span></span>|<span data-ttu-id="515f5-260">L'utilisateur a annulé l'installation.</span><span class="sxs-lookup"><span data-stu-id="515f5-260">The user canceled installation.</span></span>|  
|<span data-ttu-id="515f5-261">1603</span><span class="sxs-lookup"><span data-stu-id="515f5-261">1603</span></span>|<span data-ttu-id="515f5-262">Une erreur irrécupérable s'est produite pendant l'installation.</span><span class="sxs-lookup"><span data-stu-id="515f5-262">A fatal error occurred during installation.</span></span>|  
|<span data-ttu-id="515f5-263">1641</span><span class="sxs-lookup"><span data-stu-id="515f5-263">1641</span></span>|<span data-ttu-id="515f5-264">Un redémarrage est nécessaire pour terminer l'installation.</span><span class="sxs-lookup"><span data-stu-id="515f5-264">A restart is required to complete the installation.</span></span> <span data-ttu-id="515f5-265">Ce message indique que l'opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="515f5-265">This message indicates success.</span></span>|  
|<span data-ttu-id="515f5-266">3010</span><span class="sxs-lookup"><span data-stu-id="515f5-266">3010</span></span>|<span data-ttu-id="515f5-267">Un redémarrage est nécessaire pour terminer l'installation.</span><span class="sxs-lookup"><span data-stu-id="515f5-267">A restart is required to complete the installation.</span></span> <span data-ttu-id="515f5-268">Ce message indique que l'opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="515f5-268">This message indicates success.</span></span>|  
|<span data-ttu-id="515f5-269">5100</span><span class="sxs-lookup"><span data-stu-id="515f5-269">5100</span></span>|<span data-ttu-id="515f5-270">L'ordinateur de l'utilisateur n'a pas la configuration requise.</span><span class="sxs-lookup"><span data-stu-id="515f5-270">The user's computer does not meet system requirements.</span></span>|  
  
<a name="additional_error_codes"></a>   
### <a name="download-error-codes"></a><span data-ttu-id="515f5-271">Codes d'erreur de téléchargement</span><span class="sxs-lookup"><span data-stu-id="515f5-271">Download error codes</span></span>  
  
-   [<span data-ttu-id="515f5-272">Codes d’erreur du service de transfert intelligent en arrière-plan (BITS)</span><span class="sxs-lookup"><span data-stu-id="515f5-272">Background Intelligent Transfer Service (BITS) error codes</span></span>](http://msdn.microsoft.com/library/aa362823.aspx)  
  
-   [<span data-ttu-id="515f5-273">Codes d’erreur du moniker d’URL</span><span class="sxs-lookup"><span data-stu-id="515f5-273">URL moniker error codes</span></span>](http://msdn.microsoft.com/library/ms775145.aspx)  
  
-   [<span data-ttu-id="515f5-274">Codes d’erreur WinHttp</span><span class="sxs-lookup"><span data-stu-id="515f5-274">WinHttp error codes</span></span>](http://msdn.microsoft.com/library/aa383770.aspx)  
  
 <span data-ttu-id="515f5-275">Autres codes d'erreur :</span><span class="sxs-lookup"><span data-stu-id="515f5-275">Other error codes:</span></span>  
  
-   [<span data-ttu-id="515f5-276">Codes d’erreur Windows Installer</span><span class="sxs-lookup"><span data-stu-id="515f5-276">Windows Installer error codes</span></span>](http://msdn.microsoft.com/library/aa368542.aspx)  
  
-   [<span data-ttu-id="515f5-277">Codes de résultat de l’agent de mise à jour automatique Windows Update</span><span class="sxs-lookup"><span data-stu-id="515f5-277">Windows Update Agent result codes</span></span>](http://technet.microsoft.com/library/cc720442.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="515f5-278">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="515f5-278">See Also</span></span>  
 <span data-ttu-id="515f5-279">[Guide de déploiement pour les développeurs](../../../docs/framework/deployment/deployment-guide-for-developers.md) </span><span class="sxs-lookup"><span data-stu-id="515f5-279">[Deployment Guide for Developers](../../../docs/framework/deployment/deployment-guide-for-developers.md) </span></span>  
 [<span data-ttu-id="515f5-280">Configuration système requise</span><span class="sxs-lookup"><span data-stu-id="515f5-280">System Requirements</span></span>](../../../docs/framework/get-started/system-requirements.md)

