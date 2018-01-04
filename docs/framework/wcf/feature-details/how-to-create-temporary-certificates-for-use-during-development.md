---
title: "Comment : créer des certificats temporaires à utiliser au cours du développement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d6c955c3498c830403f628b4805611fadc44d68
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a><span data-ttu-id="9dc7d-102">Comment : créer des certificats temporaires à utiliser au cours du développement</span><span class="sxs-lookup"><span data-stu-id="9dc7d-102">How to: Create Temporary Certificates for Use During Development</span></span>
<span data-ttu-id="9dc7d-103">Lors du développement d'un service ou d'un client sécurisé à l'aide de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], il est souvent nécessaire de fournir un certificat X.509 à utiliser comme informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-103">When developing a secure service or client using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], it is often necessary to supply an X.509 certificate to be used as a credential.</span></span> <span data-ttu-id="9dc7d-104">Le certificat fait en général partie d'une chaîne de certificats dont l'autorité racine est présente dans le magasin d'Autorités de certification racines de confiance de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-104">The certificate typically is part of a chain of certificates with a root authority found in the Trusted Root Certification Authorities store of the computer.</span></span> <span data-ttu-id="9dc7d-105">Une chaîne de certificats vous permet de définir la portée d'un jeu de certificats où en général l'autorité racine provient de votre organisation ou votre division.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-105">Having a certificate chain enables you to scope a set of certificates where typically the root authority is from your organization or business unit.</span></span> <span data-ttu-id="9dc7d-106">Pour émuler ce scénario au moment du développement, vous pouvez créer deux certificats pour satisfaire les conditions de sécurité.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-106">To emulate this at development time, you can create two certificates to satisfy the security requirements.</span></span> <span data-ttu-id="9dc7d-107">Le premier est un certificat auto-signé placé dans le magasin d'Autorités de certification racines de confiance. Le deuxième certificat est créé à partir du premier et placé dans le magasin personnel de l'emplacement de l'ordinateur local ou dans le magasin personnel de l'emplacement de l'utilisateur actif.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-107">The first is a self-signed certificate that is placed in the Trusted Root Certification Authorities store, and the second certificate is created from the first and is placed in either the Personal store of the Local Machine location, or the Personal store of the Current User location.</span></span> <span data-ttu-id="9dc7d-108">Cette rubrique décrit les étapes permettant de créer ces deux certificats à l’aide de l’ [outil de création de certificat (MakeCert.exe)](http://go.microsoft.com/fwlink/?LinkId=248185), fourni par le Kit de développement logiciel (SDK) [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9dc7d-108">This topic walks through the steps to create these two certificates using the [Certificate Creation Tool (MakeCert.exe)](http://go.microsoft.com/fwlink/?LinkId=248185), which is provided by the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9dc7d-109">Les certificats générés par l'outil de création de certification sont fournis uniquement à des fins de tests.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-109">The certificates the Certification Creation tool generates are provided for testing purposes only.</span></span> <span data-ttu-id="9dc7d-110">Lorsque vous déployez un service ou un client, veillez à utiliser un certificat approprié fourni par une autorité de certification.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-110">When deploying a service or client, be sure to use an appropriate certificate provided by a certification authority.</span></span> <span data-ttu-id="9dc7d-111">Celui-ci peut provenir d'un serveur de certificat [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] dans votre organisation ou d'un tiers.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-111">This could either be from a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] certificate server in your organization or a third party.</span></span>  
>   
>  <span data-ttu-id="9dc7d-112">Par défaut, le [Makecert.exe (outil de création de certificat)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) crée des certificats dont l’autorité racine est appelée « agence de racine**. »**</span><span class="sxs-lookup"><span data-stu-id="9dc7d-112">By default, the [Makecert.exe (Certificate Creation Tool)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) creates certificates whose root authority is called "Root Agency**."**</span></span> <span data-ttu-id="9dc7d-113">Comme celle-ci ne figure pas dans le magasin d'Autorités de certification racines de confiance, ces certificats ne sont pas sécurisés.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-113">Because the "Root Agency" is not in the Trusted Root Certification Authorities store, this makes these certificates insecure.</span></span> <span data-ttu-id="9dc7d-114">La création d'un certificat auto-signé placé dans le magasin d'Autorités de certification racines de confiance vous permet de créer un environnement de développement qui reproduit plus fidèlement votre environnement de déploiement.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-114">Creating a self-signed certificate that is placed in the Trusted Root Certification Authorities store enables you to create a development environment that more closely simulates your deployment environment.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="9dc7d-115"> la création et l’utilisation de certificats, consultez [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="9dc7d-115"> creating and using certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="9dc7d-116"> l’utilisation d’un certificat en tant qu’informations d’identification, consultez [Securing Services and Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="9dc7d-116"> using a certificate as a credential, see [Securing Services and Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span></span> <span data-ttu-id="9dc7d-117">Pour obtenir un didacticiel à propos de l’utilisation de la technologie Authenticode de Microsoft, consultez [Authenticode Overviews and Tutorials](http://go.microsoft.com/fwlink/?LinkId=88919)(Vues d’ensemble et didacticiels relatifs à Authenticode).</span><span class="sxs-lookup"><span data-stu-id="9dc7d-117">For a tutorial about using Microsoft Authenticode technology, see [Authenticode Overviews and Tutorials](http://go.microsoft.com/fwlink/?LinkId=88919).</span></span>  
  
### <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a><span data-ttu-id="9dc7d-118">Pour créer un certificat d'autorité racine auto-signé et exporter la clé privée</span><span class="sxs-lookup"><span data-stu-id="9dc7d-118">To create a self-signed root authority certificate and export the private key</span></span>  
  
1.  <span data-ttu-id="9dc7d-119">Utilisez l'outil MakeCert.exe avec les commutateurs suivants :</span><span class="sxs-lookup"><span data-stu-id="9dc7d-119">Use the MakeCert.exe tool with the following switches:</span></span>  
  
    1.  <span data-ttu-id="9dc7d-120">`-n` `subjectName`.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-120">`-n` `subjectName`.</span></span> <span data-ttu-id="9dc7d-121">Spécifie le nom du sujet.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-121">Specifies the subject name.</span></span> <span data-ttu-id="9dc7d-122">La convention est de préfixer le nom du sujet avec "CN = ", abréviation de « Common Name ».</span><span class="sxs-lookup"><span data-stu-id="9dc7d-122">The convention is to prefix the subject name with "CN = " for "Common Name".</span></span>  
  
    2.  <span data-ttu-id="9dc7d-123">`-r`.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-123">`-r`.</span></span> <span data-ttu-id="9dc7d-124">Spécifie que le certificat sera auto-signé.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-124">Specifies that the certificate will be self-signed.</span></span>  
  
    3.  <span data-ttu-id="9dc7d-125">`-sv` `privateKeyFile`.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-125">`-sv` `privateKeyFile`.</span></span> <span data-ttu-id="9dc7d-126">Spécifie le fichier qui contient le conteneur de clé privée.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-126">Specifies the file that contains the private key container.</span></span>  
  
     <span data-ttu-id="9dc7d-127">Par exemple, la commande suivante crée un certificat auto-signé avec un nom de sujet de "CN=TempCA".</span><span class="sxs-lookup"><span data-stu-id="9dc7d-127">For example, the following command creates a self-signed certificate with a subject name of "CN=TempCA."</span></span>  
  
    ```  
    makecert -n "CN=TempCA" -r -sv TempCA.pvk TempCA.cer  
    ```  
  
     <span data-ttu-id="9dc7d-128">Le système vous invite à fournir un mot de passe pour protéger la clé privée.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-128">You will be prompted to provide a password to protect the private key.</span></span> <span data-ttu-id="9dc7d-129">Ce mot de passe est requis lors de la création d'un certificat signé par ce certificat racine.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-129">This password is required when creating a certificate signed by this root certificate.</span></span>  
  
### <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a><span data-ttu-id="9dc7d-130">Pour créer un nouveau certificat signé par un certificat d'autorité racine</span><span class="sxs-lookup"><span data-stu-id="9dc7d-130">To create a new certificate signed by a root authority certificate</span></span>  
  
1.  <span data-ttu-id="9dc7d-131">Utilisez l'outil MakeCert.exe avec les commutateurs suivants :</span><span class="sxs-lookup"><span data-stu-id="9dc7d-131">Use the MakeCert.exe tool with the following switches:</span></span>  
  
    1.  <span data-ttu-id="9dc7d-132">`-sk` `subjectKey`.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-132">`-sk` `subjectKey`.</span></span> <span data-ttu-id="9dc7d-133">Emplacement du conteneur de clé du sujet comportant la clé privée.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-133">The location of the subject's key container that holds the private key.</span></span> <span data-ttu-id="9dc7d-134">Un conteneur de clé sera créé s'il n'en existe aucun.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-134">If a key container does not exist, one is created.</span></span> <span data-ttu-id="9dc7d-135">Si aucune des options -sk ou -sv n'est utilisée, un conteneur de clé appelé JoeSoft est créé par défaut.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-135">If neither of the -sk or -sv options is used, a key container called JoeSoft is created by default.</span></span>  
  
    2.  <span data-ttu-id="9dc7d-136">`-n` `subjectName`.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-136">`-n` `subjectName`.</span></span> <span data-ttu-id="9dc7d-137">Spécifie le nom du sujet.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-137">Specifies the subject name.</span></span> <span data-ttu-id="9dc7d-138">La convention est de préfixer le nom du sujet avec "CN = ", abréviation de « Common Name ».</span><span class="sxs-lookup"><span data-stu-id="9dc7d-138">The convention is to prefix the subject name with "CN = " for "Common Name".</span></span>  
  
    3.  <span data-ttu-id="9dc7d-139">`-iv` `issuerKeyFile`.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-139">`-iv` `issuerKeyFile`.</span></span> <span data-ttu-id="9dc7d-140">Spécifie le fichier de clé privée de l'émetteur.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-140">Specifies the issuer's private key file.</span></span>  
  
    4.  <span data-ttu-id="9dc7d-141">`-ic` `issuerCertFile`.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-141">`-ic` `issuerCertFile`.</span></span> <span data-ttu-id="9dc7d-142">Spécifie l'emplacement du certificat de l'émetteur.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-142">Specifies the location of the issuer's certificate.</span></span>  
  
     <span data-ttu-id="9dc7d-143">Par exemple, la commande suivante crée un certificat signé par le certificat d'autorité racine `TempCA` avec `"CN=SignedByCA"` comme nom de sujet qui utilise la clé privée de l'émetteur.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-143">For example, the following command creates a certificate signed by the `TempCA` root authority certificate with a subject name of `"CN=SignedByCA"` using the private key of the issuer.</span></span>  
  
    ```  
    makecert -sk SignedByCA -iv TempCA.pvk -n "CN=SignedByCA" -ic TempCA.cer SignedByCA.cer -sr currentuser -ss My  
    ```  
  
## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a><span data-ttu-id="9dc7d-144">Installation d'un certificat dans le magasin d'Autorités de certification racines de confiance</span><span class="sxs-lookup"><span data-stu-id="9dc7d-144">Installing a Certificate in the Trusted Root Certification Authorities Store</span></span>  
 <span data-ttu-id="9dc7d-145">Une fois qu'un certificat auto-signé est créé, vous pouvez l'installer dans le magasin d'Autorités de certification racines de confiance.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-145">Once a self-signed certificate is created, you can install it in the Trusted Root Certification Authorities store.</span></span> <span data-ttu-id="9dc7d-146">Tous les certificats signés à ce stade avec le certificat sont approuvés par l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-146">Any certificates that are signed with the certificate at this point are trusted by the computer.</span></span> <span data-ttu-id="9dc7d-147">Pour cette raison, supprimez le certificat du magasin dès que vous n'en avez plus besoin.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-147">For this reason, delete the certificate from the store as soon as you no longer need it.</span></span> <span data-ttu-id="9dc7d-148">Lorsque vous supprimez ce certificat d'autorité racine, tous les autres certificats ayant signé à l'aide de ce dernier ne sont plus autorisés.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-148">When you delete this root authority certificate, all other certificates that signed with it become unauthorized.</span></span> <span data-ttu-id="9dc7d-149">Les certificats d'autorité racines sont un simple mécanisme qui permet de définir la portée d'un groupe de certificats selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-149">Root authority certificates are simply a mechanism whereby a group of certificates can be scoped as necessary.</span></span> <span data-ttu-id="9dc7d-150">Par exemple, dans les applications d'égal à égal, l'autorité racine n'est pas nécessaire le plus souvent dans la mesure où l'identité d'un individu est garantie par le certificat qu'il fournit.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-150">For example, in peer-to-peer applications, there is typically no need for a root authority because you simply trust the identity of an individual by its supplied certificate.</span></span>  
  
#### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a><span data-ttu-id="9dc7d-151">Pour installer un certificat auto-signé dans les Autorités de certification racines de confiance</span><span class="sxs-lookup"><span data-stu-id="9dc7d-151">To install a self-signed certificate in the Trusted Root Certification Authorities</span></span>  
  
1.  <span data-ttu-id="9dc7d-152">Ouvrez le composant logiciel enfichable Certificat.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-152">Open the certificate snap-in.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="9dc7d-153">[Comment : afficher des certificats avec le composant logiciel enfichable MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="9dc7d-153"> [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2.  <span data-ttu-id="9dc7d-154">Ouvrez le dossier pour stocker le certificat, soit **Ordinateur local** , soit **Utilisateur actuel**.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-154">Open the folder to store the certificate, either the **Local Computer** or the **Current User**.</span></span>  
  
3.  <span data-ttu-id="9dc7d-155">Ouvrez le dossier **Autorités de certification racines de confiance** .</span><span class="sxs-lookup"><span data-stu-id="9dc7d-155">Open the **Trusted Root Certification Authorities** folder.</span></span>  
  
4.  <span data-ttu-id="9dc7d-156">Cliquez avec le bouton droit sur le dossier **Certificats** et cliquez sur **Toutes les tâches**, puis cliquez sur **Importer**.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-156">Right-click the **Certificates** folder and click **All Tasks**, then click **Import**.</span></span>  
  
5.  <span data-ttu-id="9dc7d-157">Suivez les instructions de l'Assistant à l'écran pour importer TempCa.cer dans le magasin.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-157">Follow the on-screen wizard instructions to import the TempCa.cer into the store.</span></span>  
  
## <a name="using-certificates-with-wcf"></a><span data-ttu-id="9dc7d-158">Utilisation de certificats avec WCF</span><span class="sxs-lookup"><span data-stu-id="9dc7d-158">Using Certificates With WCF</span></span>  
 <span data-ttu-id="9dc7d-159">Une fois que vous avez configuré les certificats temporaires, vous pouvez les utiliser pour développer des solutions WCF qui spécifient des certificats comme un type d'informations d'identification du client.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-159">Once you have set up the temporary certificates, you can use them to develop WCF solutions that specify certificates as a client credential type.</span></span> <span data-ttu-id="9dc7d-160">Par exemple, la configuration XML suivante spécifie la sécurité du message et un certificat comme type d'informations d'identification du client.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-160">For example, the following XML configuration specifies message security and a certificate as the client credential type.</span></span>  
  
#### <a name="to-specify-a-certificate-as-the-client-credential-type"></a><span data-ttu-id="9dc7d-161">Pour spécifier un certificat comme type d'informations d'identification du client</span><span class="sxs-lookup"><span data-stu-id="9dc7d-161">To specify a certificate as the client credential type</span></span>  
  
-   <span data-ttu-id="9dc7d-162">Dans le fichier de configuration d'un service, utilisez le XML suivant pour affecter au mode de sécurité la valeur Message, et au type d'informations d'identification du client la valeur Certificat.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-162">In the configuration file for a service, use the following XML to set the security mode to message, and the client credential type to certificate.</span></span>  
  
    ```xml  
    <bindings>       
      <wsHttpBinding>  
        <binding name="CertificateForClient">  
          <security>  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    ```  
  
 <span data-ttu-id="9dc7d-163">Dans le fichier de configuration pour un client, utilisez le code XML suivant pour spécifier que le certificat est trouvé dans le magasin de l’utilisateur et sont accessibles via le champ SubjectName la valeur « CohoWinery ».</span><span class="sxs-lookup"><span data-stu-id="9dc7d-163">In the configuration file for a client, use the following XML to specify that the certificate is found in the user’s store, and can be found by searching the SubjectName field for the value "CohoWinery."</span></span>  
  
```xml  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="CertForClient">  
      <clientCredentials>  
        <clientCertificate findValue="CohoWinery" x509FindType="FindBySubjectName" />  
       </clientCredentials>  
     </behavior>  
   </endpointBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="9dc7d-164">Pour plus d’informations sur l’utilisation des certificats dans WCF, consultez [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="9dc7d-164">For more information about using certificates in WCF, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="9dc7d-165">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9dc7d-165">.NET Framework Security</span></span>  
 <span data-ttu-id="9dc7d-166">Veillez à supprimer tous les certificats d'autorité racines temporaires des dossiers **Autorités de certification racines de confiance** et **Personnel** en cliquant avec le bouton droit sur le certificat, en cliquant sur ensuite **Supprimer**.</span><span class="sxs-lookup"><span data-stu-id="9dc7d-166">Be sure to delete any temporary root authority certificates from the **Trusted Root Certification Authorities** and **Personal** folders by right-clicking the certificate, then clicking **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dc7d-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9dc7d-167">See Also</span></span>  
 [<span data-ttu-id="9dc7d-168">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="9dc7d-168">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="9dc7d-169">Guide pratique pour afficher des certificats à l’aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="9dc7d-169">How to: View Certificates with the MMC Snap-in</span></span>](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [<span data-ttu-id="9dc7d-170">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="9dc7d-170">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
