---
title: "Comment : configurer un port avec un certificat SSL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3fbd3b640e90ecf0ff5857bd33465e8c60135eac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="b7059-102">Comment : configurer un port avec un certificat SSL</span><span class="sxs-lookup"><span data-stu-id="b7059-102">How to: Configure a Port with an SSL Certificate</span></span>
<span data-ttu-id="b7059-103">Lors de la création d'un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] auto-hébergé à l'aide de la classe <xref:System.ServiceModel.WSHttpBinding> qui utilise la sécurité de transport, vous devez aussi configurer un port avec un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="b7059-103">When creating a self-hosted [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="b7059-104">Si vous ne créez pas de service auto-hébergé, vous pouvez héberger votre service sur les services Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="b7059-104">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="b7059-105">[Sécurité de Transport HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="b7059-105"> [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span></span>  
  
 <span data-ttu-id="b7059-106">Pour configurer un port, l'outil que vous utilisez dépend du système d'exploitation qui s'exécute sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b7059-106">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="b7059-107">Si vous exécutez [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou [!INCLUDE[wxp](../../../../includes/wxp-md.md)], utilisez l'outil HttpCfg.exe.</span><span class="sxs-lookup"><span data-stu-id="b7059-107">If you are running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool.</span></span> <span data-ttu-id="b7059-108">Avec [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], cet outil est installé.</span><span class="sxs-lookup"><span data-stu-id="b7059-108">With [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] this tool is installed.</span></span> <span data-ttu-id="b7059-109">Avec [!INCLUDE[wxp](../../../../includes/wxp-md.md)], vous pouvez télécharger l’outil à [outils de prise en charge de Windows XP Service Pack 2](http://go.microsoft.com/fwlink/?LinkId=88606).</span><span class="sxs-lookup"><span data-stu-id="b7059-109">With [!INCLUDE[wxp](../../../../includes/wxp-md.md)], you can download the tool at [Windows XP Service Pack 2 Support Tools](http://go.microsoft.com/fwlink/?LinkId=88606).</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="b7059-110">[Vue d’ensemble de Httpcfg](http://go.microsoft.com/fwlink/?LinkId=88605).</span><span class="sxs-lookup"><span data-stu-id="b7059-110"> [Httpcfg Overview](http://go.microsoft.com/fwlink/?LinkId=88605).</span></span> <span data-ttu-id="b7059-111">Le [documentation des outils de Support Windows](http://go.microsoft.com/fwlink/?LinkId=94840) explique la syntaxe de l’outil Httpcfg.exe.</span><span class="sxs-lookup"><span data-stu-id="b7059-111">The [Windows Support Tools documentation](http://go.microsoft.com/fwlink/?LinkId=94840) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="b7059-112">Si vous exécutez [!INCLUDE[wv](../../../../includes/wv-md.md)], utilisez l'outil Netsh.exe qui est déjà installé.</span><span class="sxs-lookup"><span data-stu-id="b7059-112">If you are running [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool that is already installed.</span></span>  
  
 <span data-ttu-id="b7059-113">Cette rubrique décrit comment exécuter plusieurs procédures :</span><span class="sxs-lookup"><span data-stu-id="b7059-113">This topic describes how to accomplish several procedures:</span></span>  
  
-   <span data-ttu-id="b7059-114">Détermination de la configuration de port actuelle d'un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b7059-114">Determining a computer's current port configuration.</span></span>  
  
-   <span data-ttu-id="b7059-115">Obtention de l'empreinte numérique d'un certificat (nécessaire pour les deux procédures suivantes).</span><span class="sxs-lookup"><span data-stu-id="b7059-115">Getting a certificate's thumbprint (necessary for the following two procedures).</span></span>  
  
-   <span data-ttu-id="b7059-116">Liaison d'un certificat SSL à une configuration de port.</span><span class="sxs-lookup"><span data-stu-id="b7059-116">Binding an SSL certificate to a port configuration.</span></span>  
  
-   <span data-ttu-id="b7059-117">Liaison d'un certificat SSL à une configuration de port et prise en charge des certificats clients.</span><span class="sxs-lookup"><span data-stu-id="b7059-117">Binding an SSL certificate to a port configuration and supporting client certificates.</span></span>  
  
-   <span data-ttu-id="b7059-118">Suppression d'un certificat SSL d'un numéro de port.</span><span class="sxs-lookup"><span data-stu-id="b7059-118">Deleting an SSL certificate from a port number.</span></span>  
  
 <span data-ttu-id="b7059-119">Notez que la modification des certificats stockés sur l'ordinateur requiert des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="b7059-119">Note that modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
### <a name="to-determine-how-ports-are-configured"></a><span data-ttu-id="b7059-120">Pour déterminer comment sont configurés les ports</span><span class="sxs-lookup"><span data-stu-id="b7059-120">To determine how ports are configured</span></span>  
  
1.  <span data-ttu-id="b7059-121">Dans [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou [!INCLUDE[wxp](../../../../includes/wxp-md.md)], utilisez l’outil HttpCfg.exe pour afficher la configuration du port en cours, à l’aide de la **requête** et **ssl** bascule, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b7059-121">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```  
    httpcfg query ssl  
    ```  
  
2.  <span data-ttu-id="b7059-122">Dans [!INCLUDE[wv](../../../../includes/wv-md.md)], utilisez l'outil Netsh.exe pour consulter la configuration de port actuelle, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b7059-122">In [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```  
    netsh http show sslcert  
    ```  
  
### <a name="to-get-a-certificates-thumbprint"></a><span data-ttu-id="b7059-123">Pour obtenir l'empreinte numérique d'un certificat</span><span class="sxs-lookup"><span data-stu-id="b7059-123">To get a certificate's thumbprint</span></span>  
  
1.  <span data-ttu-id="b7059-124">Utilisez le composant logiciel enfichable MMC Certificats pour rechercher un certificat X.509 ayant pour objectif l'authentification du client.</span><span class="sxs-lookup"><span data-stu-id="b7059-124">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="b7059-125">[Comment : afficher des certificats avec le composant logiciel enfichable MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="b7059-125"> [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2.  <span data-ttu-id="b7059-126">Accédez à l'empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="b7059-126">Access the certificate's thumbprint.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="b7059-127">[Comment : récupérer l’empreinte numérique d’un certificat](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="b7059-127"> [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3.  <span data-ttu-id="b7059-128">Copiez l'empreinte numérique du certificat dans un éditeur de texte, tel que le Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="b7059-128">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4.  <span data-ttu-id="b7059-129">Supprimez tous les espaces entre les caractères hexadécimaux.</span><span class="sxs-lookup"><span data-stu-id="b7059-129">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="b7059-130">Pour ce faire, vous pouvez utiliser la fonctionnalité rechercher et remplacer de l'éditeur de texte pour remplacer chaque espace par un caractère Null.</span><span class="sxs-lookup"><span data-stu-id="b7059-130">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="b7059-131">Pour lier un certificat SSL à un numéro de port</span><span class="sxs-lookup"><span data-stu-id="b7059-131">To bind an SSL certificate to a port number</span></span>  
  
1.  <span data-ttu-id="b7059-132">Dans [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou [!INCLUDE[wxp](../../../../includes/wxp-md.md)], utilisez l'outil HttpCfg.exe en mode « défini » dans le magasin SSL (Secure Sockets Layer) pour lier le certificat à un numéro de port.</span><span class="sxs-lookup"><span data-stu-id="b7059-132">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="b7059-133">L'outil utilise l'empreinte numérique pour identifier le certificat, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b7059-133">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    -   <span data-ttu-id="b7059-134">Le **-i** commutateur possède la syntaxe de `IP`:`port` et indique à l’outil pour définir le certificat sur le port 8012 de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b7059-134">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="b7059-135">Le cas échéant, les quatre zéros qui précédent le nombre peuvent aussi être remplacés par l'adresse IP réelle de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b7059-135">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    -   <span data-ttu-id="b7059-136">Le **-h** commutateur spécifie l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="b7059-136">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2.  <span data-ttu-id="b7059-137">Dans [!INCLUDE[wv](../../../../includes/wv-md.md)], utilisez l'outil Netsh.exe, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b7059-137">In [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    -   <span data-ttu-id="b7059-138">Le **certhash** paramètre spécifie l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="b7059-138">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    -   <span data-ttu-id="b7059-139">Le **port** paramètre spécifie l’adresse IP et le port, et fonctionne exactement comme le **-i** switch de l’outil Httpcfg.exe décrit.</span><span class="sxs-lookup"><span data-stu-id="b7059-139">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    -   <span data-ttu-id="b7059-140">Le **appid** paramètre est un GUID qui peut être utilisé pour identifier l’application propriétaire.</span><span class="sxs-lookup"><span data-stu-id="b7059-140">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="b7059-141">Pour lier un certificat SSL à un numéro de port et prendre en charge les certificats clients</span><span class="sxs-lookup"><span data-stu-id="b7059-141">To bind an SSL certificate to a port number and support client certificates</span></span>  
  
1.  <span data-ttu-id="b7059-142">Dans [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou [!INCLUDE[wxp](../../../../includes/wxp-md.md)], pour prendre en charge les clients authentifiés avec les certificats X.509 au niveau de la couche de transport, suivez la procédure précédente mais passez un paramètre de ligne de commande supplémentaire à HttpCfg.exe, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b7059-142">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="b7059-143">Le **-f** commutateur possède la syntaxe de `n` où n est un nombre compris entre 1 et 7.</span><span class="sxs-lookup"><span data-stu-id="b7059-143">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="b7059-144">Une valeur de 2, comme indiqué dans l'exemple précédent, active des certificats clients au niveau de la couche de transport.</span><span class="sxs-lookup"><span data-stu-id="b7059-144">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="b7059-145">La valeur 3 active les certificats clients et mappe ces certificats à un compte Windows.</span><span class="sxs-lookup"><span data-stu-id="b7059-145">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="b7059-146">Consultez l'aide de HttpCfg.exe pour connaître le comportement des autres valeurs.</span><span class="sxs-lookup"><span data-stu-id="b7059-146">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2.  <span data-ttu-id="b7059-147">Dans [!INCLUDE[wv](../../../../includes/wv-md.md)], pour prendre en charge les clients authentifiés avec les certificats X.509 au niveau de la couche de transport, suivez la procédure précédente mais avec un paramètre supplémentaire, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b7059-147">In [!INCLUDE[wv](../../../../includes/wv-md.md)], to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### <a name="to-delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="b7059-148">Pour supprimer un certificat SSL d'un numéro de port</span><span class="sxs-lookup"><span data-stu-id="b7059-148">To delete an SSL certificate from a port number</span></span>  
  
1.  <span data-ttu-id="b7059-149">Utilisez l'outil HttpCfg.exe ou Netsh.exe pour consulter les ports et les empreintes numériques de toutes les liaisons sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b7059-149">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="b7059-150">Pour imprimer les informations sur le disque, utilisez le caractère de redirection « > », comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b7059-150">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```  
    httpcfg query ssl>myMachinePorts.txt  
    ```  
  
2.  <span data-ttu-id="b7059-151">Dans [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou [!INCLUDE[wxp](../../../../includes/wxp-md.md)], utilisez l’outil HttpCfg.exe avec les **supprimer** et **ssl** mots clés.</span><span class="sxs-lookup"><span data-stu-id="b7059-151">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="b7059-152">Utilisez le **-i** commutateur pour spécifier le `IP`:`port` nombre et le **-h** commutateur pour spécifier l’empreinte numérique.</span><span class="sxs-lookup"><span data-stu-id="b7059-152">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3.  <span data-ttu-id="b7059-153">Dans [!INCLUDE[wv](../../../../includes/wv-md.md)], utilisez l'outil Netsh.exe, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b7059-153">In [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="b7059-154">Exemple</span><span class="sxs-lookup"><span data-stu-id="b7059-154">Example</span></span>  
 <span data-ttu-id="b7059-155">Le code suivant montre comment créer un service auto-hébergé à l'aide de la classe <xref:System.ServiceModel.WSHttpBinding> à laquelle est attribuée la sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="b7059-155">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="b7059-156">Lorsque vous créez une application, spécifiez le numéro de port dans l'adresse.</span><span class="sxs-lookup"><span data-stu-id="b7059-156">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="b7059-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7059-157">See Also</span></span>  
 [<span data-ttu-id="b7059-158">Sécurité de transport HTTP</span><span class="sxs-lookup"><span data-stu-id="b7059-158">HTTP Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
