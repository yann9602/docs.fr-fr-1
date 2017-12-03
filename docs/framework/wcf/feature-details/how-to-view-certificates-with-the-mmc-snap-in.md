---
title: "Comment : afficher des certificats à l'aide du composant logiciel enfichable MMC"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5981e68ebe2870870fff5e92e87d7582ac2c42b5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="b5fcd-102">Comment : afficher des certificats à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="b5fcd-102">How to: View Certificates with the MMC Snap-in</span></span>
<span data-ttu-id="b5fcd-103">Le certificat X.509 est un type courant d'information d'identification.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-103">A common type of credential is the X.509 certificate.</span></span> <span data-ttu-id="b5fcd-104">Lorsque vous créez des clients ou des services sécurisés, vous pouvez spécifier l'utilisation d'un certificat comme informations d'identification de client ou de service en utilisant des méthodes telles que <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-104">When creating secure services or clients, you can specify a certificate be used as the client or service credential by using methods such as the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method.</span></span> <span data-ttu-id="b5fcd-105">Cette méthode requiert divers paramètres, tels que le magasin dans lequel le certificat est stocké ainsi qu'une valeur à utiliser lorsque vous recherchez ce certificat.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-105">The method requires various parameters, such as the store where the certificate is stored and a value to use when searching for the certificate.</span></span> <span data-ttu-id="b5fcd-106">La procédure suivante montre comment rechercher un certificat approprié dans les magasins d'un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-106">The following procedure demonstrates how to examine the stores on a computer to find an appropriate certificate.</span></span> <span data-ttu-id="b5fcd-107">Pour obtenir un exemple de recherche de l’empreinte de certificat, consultez [Comment : récupérer l’empreinte numérique d’un certificat](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="b5fcd-107">For an example of finding the certificate thumbprint, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
### <a name="to-view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="b5fcd-108">Pour afficher des certificats dans le composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="b5fcd-108">To view certificates in the MMC snap-in</span></span>  
  
1.  <span data-ttu-id="b5fcd-109">Ouvrez une fenêtre Invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-109">Open a Command Prompt window.</span></span>  
  
2.  <span data-ttu-id="b5fcd-110">Type `mmc` et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-110">Type `mmc` and press the ENTER key.</span></span> <span data-ttu-id="b5fcd-111">Notez que pour afficher des certificats dans le magasin de l'ordinateur local, vous devez être dans le rôle Administrateur.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-111">Note that to view certificates in the local machine store, you must be in the Administrator role.</span></span>  
  
3.  <span data-ttu-id="b5fcd-112">Sur le **fichier** menu, cliquez sur **ajouter/supprimer un composant logiciel enfichable**.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-112">On the **File** menu, click **Add/Remove Snap In**.</span></span>  
  
4.  <span data-ttu-id="b5fcd-113">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-113">Click **Add**.</span></span>  
  
5.  <span data-ttu-id="b5fcd-114">Dans le **ajouter Standalone Snap-in** boîte de dialogue, sélectionnez **certificats**.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-114">In the **Add Standalone Snap-in** dialog box, select **Certificates**.</span></span>  
  
6.  <span data-ttu-id="b5fcd-115">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-115">Click **Add**.</span></span>  
  
7.  <span data-ttu-id="b5fcd-116">Dans le **enfichable Certificats** boîte de dialogue, sélectionnez **compte d’ordinateur** et cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-116">In the **Certificates snap-in** dialog box, select **Computer account** and click **Next**.</span></span> <span data-ttu-id="b5fcd-117">Si vous le souhaitez, vous pouvez sélectionner **mon compte d’utilisateur** ou **compte de Service**.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-117">Optionally, you can select **My User account** or **Service account**.</span></span> <span data-ttu-id="b5fcd-118">Si vous n'êtes pas administrateur de l'ordinateur, vous pouvez uniquement gérer les certificats de votre compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-118">If you are not an administrator of the computer, you can manage certificates only for your user account.</span></span>  
  
8.  <span data-ttu-id="b5fcd-119">Dans le **sélectionner un ordinateur** boîte de dialogue, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-119">In the **Select Computer** dialog box, click **Finish**.</span></span>  
  
9. <span data-ttu-id="b5fcd-120">Dans le **ajouter Standalone Snap-in** boîte de dialogue, cliquez sur **fermer**.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-120">In the **Add Standalone Snap-in** dialog box, click **Close**.</span></span>  
  
10. <span data-ttu-id="b5fcd-121">Sur le **ajouter/supprimer un composant logiciel enfichable** boîte de dialogue, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-121">On the **Add/Remove Snap-in** dialog box, click **OK**.</span></span>  
  
11. <span data-ttu-id="b5fcd-122">Dans le **racine de la Console** fenêtre, cliquez sur **certificats (ordinateur Local)** pour afficher le certificat des magasins pour l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-122">In the **Console Root** window, click **Certificates (Local Computer)** to view the certificate stores for the computer.</span></span>  
  
12. <span data-ttu-id="b5fcd-123">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-123">Optional.</span></span> <span data-ttu-id="b5fcd-124">Pour consulter des certificats pour votre compte, répétez les étapes 3 à 6.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-124">To view certificates for your account, repeat steps 3 to 6.</span></span> <span data-ttu-id="b5fcd-125">À l’étape 7, au lieu de sélectionner **compte d’ordinateur**, cliquez sur **mon compte d’utilisateur** et répétez les étapes 8 à 10.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-125">In step 7, instead of selecting **Computer account**, click **My User account** and repeat steps 8 to 10.</span></span>  
  
13. <span data-ttu-id="b5fcd-126">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-126">Optional.</span></span> <span data-ttu-id="b5fcd-127">Sur le **fichier** menu, cliquez sur **enregistrer** ou **Enregistrer sous**.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-127">On the **File** menu, click **Save** or **Save As**.</span></span> <span data-ttu-id="b5fcd-128">Enregistrez le fichier de console pour une utilisation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-128">Save the console file for later reuse.</span></span>  
  
## <a name="viewing-certificates-with-internet-explorer"></a><span data-ttu-id="b5fcd-129">Affichage de certificats à l'aide d'Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="b5fcd-129">Viewing Certificates with Internet Explorer</span></span>  
 <span data-ttu-id="b5fcd-130">Vous pouvez également afficher, exporter, importer et supprimer des certificats à l'aide d'Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-130">You can also view, export, import, and delete certificates by using Internet Explorer.</span></span>  
  
#### <a name="to-view-certificates-with-internet-explorer"></a><span data-ttu-id="b5fcd-131">Pour afficher des certificats à l'aide d'Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="b5fcd-131">To view certificates with Internet Explorer</span></span>  
  
1.  <span data-ttu-id="b5fcd-132">Dans Internet Explorer, cliquez sur **outils**, puis cliquez sur **Options Internet** pour afficher les **Options Internet** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-132">In Internet Explorer, click **Tools**, then click **Internet Options** to display the **Internet Options** dialog box.</span></span>  
  
2.  <span data-ttu-id="b5fcd-133">Cliquez sur le **contenu** onglet.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-133">Click the **Content** tab.</span></span>  
  
3.  <span data-ttu-id="b5fcd-134">Sous **certificats**, cliquez sur **certificats**.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-134">Under **Certificates**, click **Certificates**.</span></span>  
  
4.  <span data-ttu-id="b5fcd-135">Pour afficher les détails d’un certificat, sélectionnez le certificat, cliquez sur **vue**.</span><span class="sxs-lookup"><span data-stu-id="b5fcd-135">To view details of any certificate, select the certificate and click **View**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5fcd-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5fcd-136">See Also</span></span>  
 [<span data-ttu-id="b5fcd-137">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="b5fcd-137">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="b5fcd-138">Comment : créer des certificats temporaires à utiliser pendant le développement</span><span class="sxs-lookup"><span data-stu-id="b5fcd-138">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)  
 [<span data-ttu-id="b5fcd-139">Comment : récupérer l’empreinte numérique d’un certificat</span><span class="sxs-lookup"><span data-stu-id="b5fcd-139">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
