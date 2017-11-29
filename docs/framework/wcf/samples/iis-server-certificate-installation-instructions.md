---
title: Instructions d'installation du certificat de serveur des services Internet (IIS)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4b9496d471ca262e640c927619ccea8e4b4f4145
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a><span data-ttu-id="4c630-102">Instructions d'installation du certificat de serveur des services Internet (IIS)</span><span class="sxs-lookup"><span data-stu-id="4c630-102">Internet Information Services (IIS) Server Certificate Installation Instructions</span></span>
<span data-ttu-id="4c630-103">Pour pouvoir exécuter les exemples qui utilisent la communication sécurisée avec les services Internet (IIS), vous devez créer et installer un certificat de serveur.</span><span class="sxs-lookup"><span data-stu-id="4c630-103">To run the samples that securely communicate with Internet Information Services (IIS), you must create and install a server certificate.</span></span>  
  
## <a name="step-1-creating-certificates"></a><span data-ttu-id="4c630-104">Étape 1.</span><span class="sxs-lookup"><span data-stu-id="4c630-104">Step 1.</span></span> <span data-ttu-id="4c630-105">Création de certificats</span><span class="sxs-lookup"><span data-stu-id="4c630-105">Creating Certificates</span></span>  
 <span data-ttu-id="4c630-106">Pour créer un certificat pour votre ordinateur, ouvrez une invite de commandes de Visual studio avec des privilèges d'administrateur, puis exécutez le fichier Setup.bat inclus dans chacun des exemples qui utilisent la communication sécurisée avec IIS.</span><span class="sxs-lookup"><span data-stu-id="4c630-106">To create a certificate for your computer, open a Visual Studio command prompt with administrator privileges and run the Setup.bat that is included in each of the samples that use secure communication with IIS.</span></span> <span data-ttu-id="4c630-107">Vérifiez que le chemin d'accès inclut le dossier qui contient Makecert.exe avant d'exécuter ce fichier batch.</span><span class="sxs-lookup"><span data-stu-id="4c630-107">Ensure that the path includes the folder that contains Makecert.exe before you run this batch file.</span></span> <span data-ttu-id="4c630-108">La commande suivante permet de créer le certificat dans Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="4c630-108">The following command is used to create the certificate in Setup.bat.</span></span>  
  
```  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a><span data-ttu-id="4c630-109">Étape 2.</span><span class="sxs-lookup"><span data-stu-id="4c630-109">Step 2.</span></span> <span data-ttu-id="4c630-110">Installation de certificats</span><span class="sxs-lookup"><span data-stu-id="4c630-110">Installing Certificates</span></span>  
 <span data-ttu-id="4c630-111">La procédure d'installation des certificats que vous venez de créer varie en fonction de la version d'IIS utilisée.</span><span class="sxs-lookup"><span data-stu-id="4c630-111">The steps required to install the certificates you just created depend on which version of IIS you are using.</span></span>  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a><span data-ttu-id="4c630-112">Pour installer IIS sur IIS 5.1 (Windows XP) et IIS 6.0 (Windows Server 2003)</span><span class="sxs-lookup"><span data-stu-id="4c630-112">To install IIS on IIS 5.1 (Windows XP) and IIS 6.0 (Windows Server 2003)</span></span>  
  
1.  <span data-ttu-id="4c630-113">Ouvrez le composant logiciel enfichable MMC du Gestionnaire des services IIS.</span><span class="sxs-lookup"><span data-stu-id="4c630-113">Open the Internet Information Services Manager MMC Snap-In.</span></span>  
  
2.  <span data-ttu-id="4c630-114">Cliquez sur le site Web par défaut et sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="4c630-114">Right-click the default Web site and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="4c630-115">Sélectionnez le **sécurité du répertoire** onglet.</span><span class="sxs-lookup"><span data-stu-id="4c630-115">Select the **Directory Security** tab.</span></span>  
  
4.  <span data-ttu-id="4c630-116">Cliquez sur le **certificat de serveur** bouton.</span><span class="sxs-lookup"><span data-stu-id="4c630-116">Click the **Server Certificate** button.</span></span> <span data-ttu-id="4c630-117">L’Assistant de création de certificats de serveur web démarre.</span><span class="sxs-lookup"><span data-stu-id="4c630-117">The Web Server Certificate Wizard starts.</span></span>  
  
5.  <span data-ttu-id="4c630-118">Terminez l'Assistant.</span><span class="sxs-lookup"><span data-stu-id="4c630-118">Complete the wizard.</span></span> <span data-ttu-id="4c630-119">Sélectionnez l'option d'assignation de certificat.</span><span class="sxs-lookup"><span data-stu-id="4c630-119">Select the option to assign a certificate.</span></span> <span data-ttu-id="4c630-120">Sélectionnez le certificat ServiceModelSamples-HTTPS-Server dans la liste de certificats qui s'affiche.</span><span class="sxs-lookup"><span data-stu-id="4c630-120">Select the ServiceModelSamples-HTTPS-Server certificate from the list of certificates that are displayed.</span></span>  
  
     <span data-ttu-id="4c630-121">![Assistant certificat de IIS](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span><span class="sxs-lookup"><span data-stu-id="4c630-121">![IIS Certificate Wizard](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span></span>  
  
6.  <span data-ttu-id="4c630-122">Testez l'accès au service dans un navigateur, en utilisant l'adresse HTTPS suivante : https://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="4c630-122">Test access to the service in a browser by using the HTTPS address https://localhost/servicemodelsamples/service.svc.</span></span>  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a><span data-ttu-id="4c630-123">Si SSL a été configuré précédemment via l'utilisation du fichier Httpcfg.exe :</span><span class="sxs-lookup"><span data-stu-id="4c630-123">If SSL was previously configured by using Httpcfg.exe</span></span>  
  
1.  <span data-ttu-id="4c630-124">Utilisez Makecert.exe (ou exécutez Setup.bat) pour créer le certificat de serveur.</span><span class="sxs-lookup"><span data-stu-id="4c630-124">Use Makecert.exe (or run Setup.bat) to create the server certificate.</span></span>  
  
2.  <span data-ttu-id="4c630-125">Exécutez le Gestionnaire des services IIS et installez le certificat conformément aux instructions des étapes précédentes.</span><span class="sxs-lookup"><span data-stu-id="4c630-125">Run the IIS manager and install the certificate according to the previous steps.</span></span>  
  
3.  <span data-ttu-id="4c630-126">Ajoutez la ligne de code suivante au programme client :</span><span class="sxs-lookup"><span data-stu-id="4c630-126">Add the following line of code to the client program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4c630-127">Ce code est uniquement requis pour les certificats de test tels que ceux créés par Makecert.exe.</span><span class="sxs-lookup"><span data-stu-id="4c630-127">This code is only required for test certificates such as those created by Makecert.exe.</span></span> <span data-ttu-id="4c630-128">Il n'est pas recommandé pour le code de production.</span><span class="sxs-lookup"><span data-stu-id="4c630-128">It is not recommended for production code.</span></span>  
  
```  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a><span data-ttu-id="4c630-129">Pour installer IIS sur IIS 7.0 (Windows Vista et Windows Server 2008)</span><span class="sxs-lookup"><span data-stu-id="4c630-129">To install IIS on IIS 7.0 (Windows Vista and Windows Server 2008)</span></span>  
  
1.  <span data-ttu-id="4c630-130">À partir de la **Démarrer** menu, cliquez sur **exécuter**, puis tapez **inetmgr** pour ouvrir le composant logiciel enfichable MMC Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="4c630-130">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2.  <span data-ttu-id="4c630-131">Cliquez sur le **Site Web par défaut** et sélectionnez **modifier les liaisons...**</span><span class="sxs-lookup"><span data-stu-id="4c630-131">Right-click the **Default Web Site** and select **Edit Bindings…**</span></span>  
  
3.  <span data-ttu-id="4c630-132">Cliquez sur le **ajouter** bouton de la **liaisons de Site** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="4c630-132">Click the **Add** button of the **Site Bindings** dialog box.</span></span>  
  
4.  <span data-ttu-id="4c630-133">Sélectionnez **HTTPS** à partir de la **Type** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="4c630-133">Select **HTTPS** from the **Type** drop-down list.</span></span>  
  
5.  <span data-ttu-id="4c630-134">Sélectionnez le **ServiceModelSamples-HTTPS-Server** à partir de la **certificat SSL** liste déroulante, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4c630-134">Select the **ServiceModelSamples-HTTPS-Server** from the **SSL certificate** drop-down list and click **OK**.</span></span>  
  
6.  <span data-ttu-id="4c630-135">Testez l'accès au service dans un navigateur, en utilisant l'adresse HTTPS suivante : https://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="4c630-135">Test access to the service in a browser by using the HTTPS address https://localhost/servicemodelsamples/service.svc.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c630-136">Étant donné que le certificat de test que vous venez d'installer n'est pas un certificat approuvé, vous risquez de recevoir des avertissements de sécurité Internet Explorer supplémentaires lorsque vous recherchez des adresses Web locales sécurisées à l'aide de ce certificat.</span><span class="sxs-lookup"><span data-stu-id="4c630-136">Because the test certificate you have just installed is not a trusted certificate, you may encounter additional Internet Explorer security warnings when browsing to local Web addresses secured with this certificate.</span></span>  
  
## <a name="removing-certificates"></a><span data-ttu-id="4c630-137">Suppression de certificats</span><span class="sxs-lookup"><span data-stu-id="4c630-137">Removing Certificates</span></span>  
  
-   <span data-ttu-id="4c630-138">Utilisez le Gestionnaire des services IIS comme indiqué précédemment, mais supprimez le certificat ou la liaison au lieu de l'ajouter.</span><span class="sxs-lookup"><span data-stu-id="4c630-138">Use the Internet Information Services Manager as previously directed, but remove the certificate or binding instead of adding it.</span></span>  
  
-   <span data-ttu-id="4c630-139">Supprimez le certificat d'ordinateur en utilisant la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="4c630-139">Remove the computer certificate by using the following command.</span></span>  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
