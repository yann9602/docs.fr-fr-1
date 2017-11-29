---
title: FindPrivateKey
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c1ff00bead6130601070ac94686ee9622a6fe218
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="findprivatekey"></a><span data-ttu-id="3e49f-102">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="3e49f-102">FindPrivateKey</span></span>
<span data-ttu-id="3e49f-103">Il peut être difficile de rechercher l'emplacement et le nom du fichier de clé privée associé à un certificat X.509 spécifique dans le magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="3e49f-103">It can be difficult to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span> <span data-ttu-id="3e49f-104">L'outil FindPrivateKey.exe facilite ce processus.</span><span class="sxs-lookup"><span data-stu-id="3e49f-104">The FindPrivateKey.exe tool facilitates this process.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3e49f-105">FindPrivateKey est un exemple qui doit être compilé avant son utilisation.</span><span class="sxs-lookup"><span data-stu-id="3e49f-105">FindPrivateKey is a sample that needs to be compiled prior to use.</span></span> <span data-ttu-id="3e49f-106">Consultez la section « pour générer le projet FindPrivateKey » ci-dessous pour obtenir des instructions sur la création de l’outil FindPrivateKey.</span><span class="sxs-lookup"><span data-stu-id="3e49f-106">See the "To build the FindPrivateKey project" section below for instructions on how to build the FindPrivateKey tool.</span></span>  
  
 <span data-ttu-id="3e49f-107">Les certificats X.509 sont installés par un administrateur ou tout utilisateur sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3e49f-107">X.509 certificates are installed by an Administrator or any user in the machine.</span></span> <span data-ttu-id="3e49f-108">Cependant, le certificat peut être consulté par un service qui s'exécute sous un compte différent (par exemple, le compte ASPNET sur [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ou le compte SERVICE RÉSEAU sur [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="3e49f-108">However the certificate may be accessed by a service running under a different account (for example, the ASPNET on [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or the NETWORK SERVICE accounts on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]).</span></span>  
  
 <span data-ttu-id="3e49f-109">Ce compte peut ne pas avoir accès au fichier de clé privée parce qu'il n'a pas installé le certificat à l'origine.</span><span class="sxs-lookup"><span data-stu-id="3e49f-109">This account may not have access to the private key file because the certificate was not installed by it originally.</span></span> <span data-ttu-id="3e49f-110">L'outil FindPrivateKey vous donne l'emplacement du fichier de clé privée d'un certificat X.509 donné.</span><span class="sxs-lookup"><span data-stu-id="3e49f-110">The FindPrivateKey tool gives you the location of a given X.509 Certificate's private key file.</span></span> <span data-ttu-id="3e49f-111">Vous pouvez ajouter ou supprimer des autorisations à ce fichier une fois que vous connaissez l'emplacement du fichier de clé privée des certificats X.509 particuliers.</span><span class="sxs-lookup"><span data-stu-id="3e49f-111">You can add permissions or remove permissions to this file once you know the location of the particular X.509 certificates' private key file.</span></span>  
  
 <span data-ttu-id="3e49f-112">Les exemples qui utilisent des certificats pour la sécurité utilisent l'outil FindPrivateKey dans le fichier Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="3e49f-112">The samples that use certificates for security use the FindPrivateKey tool in the Setup.bat file.</span></span> <span data-ttu-id="3e49f-113">Une fois que le fichier de clé privée a été trouvé, vous pouvez utiliser des autres outils tels que Cacls.exe pour définir les droits d'accès appropriés sur le fichier.</span><span class="sxs-lookup"><span data-stu-id="3e49f-113">Once the private key file has been found you can use other tools such as Cacls.exe to set the appropriate access rights onto the file.</span></span>  
  
 <span data-ttu-id="3e49f-114">Lors de l'exécution d'un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sous un compte d'utilisateur, tel qu'un fichier exécutable auto-hébergé, vérifiez que le compte d'utilisateur dispose d'un accès en lecture seule au fichier.</span><span class="sxs-lookup"><span data-stu-id="3e49f-114">When running a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service under a user account, such as a self-hosted executable, ensure that the user account has read-only access to the file.</span></span> <span data-ttu-id="3e49f-115">Lors de l'exécution d'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sous IIS (Internet Information Services), les comptes par défaut sous lesquels le service s'exécute sont ASPNET sur [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ou SERVICE RESEAU sur [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] qui, par défaut, n'ont pas accès au fichier de clé privée.</span><span class="sxs-lookup"><span data-stu-id="3e49f-115">When running a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service under Internet Information Services (IIS) the default accounts that the service runs under are the ASPNET on [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or the NETWORK SERVICE on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], which by default do not have access to the private key file.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="3e49f-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="3e49f-116">Examples</span></span>  
 <span data-ttu-id="3e49f-117">Lorsque vous accédez à un certificat pour lequel le processus n'a pas de privilège d'accès en lecture, vous voyez un message d'exception semblable à l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="3e49f-117">When accessing a certificate for which the process does not have read privilege, you see an exception message similar to the following example.</span></span>  
  
```  
System.ArgumentException was unhandled  
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."  
Source="System.ServiceModel"  
```  
  
 <span data-ttu-id="3e49f-118">Lorsque cela se produit, utilisez l'outil FindPrivateKey pour rechercher le fichier de clé privée, puis définissez le droit d'accès pour le processus sous lequel le service s'exécute.</span><span class="sxs-lookup"><span data-stu-id="3e49f-118">When this occurs use the FindPrivateKey tool to find the private key file and then set the access right for the process that the service is running under.</span></span> <span data-ttu-id="3e49f-119">Cela peut être fait avec l'outil Cacls.exe, comme le montre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="3e49f-119">For example, this can be done with the Cacls.exe tool as shown in the following example.</span></span>  
  
```  
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
```  
  
#### <a name="to-build-the-findprivatekey-project"></a><span data-ttu-id="3e49f-120">Pour générer le projet FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="3e49f-120">To build the FindPrivateKey project</span></span>  
  
1.  <span data-ttu-id="3e49f-121">Ouvrez l'[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] et sélectionnez le sous-répertoire spécifique à une langue se trouvant sous l'emplacement d'installation de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="3e49f-121">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the language-specific subdirectory under the directory location where you installed the sample.</span></span>  
  
2.  <span data-ttu-id="3e49f-122">Double-cliquez sur l'icône du fichier .sln pour ouvrir ce dernier dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3e49f-122">Double-click the .sln file icon to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="3e49f-123">Dans le **générer** menu, sélectionnez **régénérer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="3e49f-123">In the **Build** menu, select **Rebuild Solution**.</span></span> <span data-ttu-id="3e49f-124">Les fichiers de programme du client sont générés dans client\bin, et les fichiers de programme du service sont générés dans service\bin.</span><span class="sxs-lookup"><span data-stu-id="3e49f-124">The client program files are built to client\bin and the service program files are built to service\bin.</span></span>  
  
4.  <span data-ttu-id="3e49f-125">La génération de la solution génère le fichier : FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="3e49f-125">Building the solution generates the file: FindPrivateKey.exe.</span></span>  
  
## <a name="conventionscommand-line-entries"></a><span data-ttu-id="3e49f-126">Entrées de lignes de commande - Conventions</span><span class="sxs-lookup"><span data-stu-id="3e49f-126">Conventions—Command-Line Entries</span></span>  
 <span data-ttu-id="3e49f-127">« [*option*] » représente un ensemble facultatif de paramètres.</span><span class="sxs-lookup"><span data-stu-id="3e49f-127">"[*option*]" represents an optional set of parameters.</span></span>  
  
 <span data-ttu-id="3e49f-128">« {*option*} » représente un jeu obligatoire de paramètres.</span><span class="sxs-lookup"><span data-stu-id="3e49f-128">"{*option*}" represents a mandatory set of parameters.</span></span>  
  
 <span data-ttu-id="3e49f-129">«*option1* &#124; *option2*« représente un choix entre des ensembles d’options.</span><span class="sxs-lookup"><span data-stu-id="3e49f-129">"*option1* &#124; *option2*" represents a choice between sets of options.</span></span>  
  
 <span data-ttu-id="3e49f-130">«\<*valeur*> » représente une valeur de paramètre doit être entré.</span><span class="sxs-lookup"><span data-stu-id="3e49f-130">"\<*value*>" represents a parameter value to be entered.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="3e49f-131">Utilisation</span><span class="sxs-lookup"><span data-stu-id="3e49f-131">Usage</span></span>  
  
```  
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]  
```  
  
 <span data-ttu-id="3e49f-132">Où :</span><span class="sxs-lookup"><span data-stu-id="3e49f-132">Where:</span></span>  
  
```  
       <subjectName> The subject name of the certificate  
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)  
       -f            output file name only  
       -d            output directory only  
       -a            output absolute file name  
```  
  
 <span data-ttu-id="3e49f-133">Si aucun paramètre n'est spécifié à l'invite de commandes, ce texte d'aide s'affiche.</span><span class="sxs-lookup"><span data-stu-id="3e49f-133">If no parameters are specified at the command prompt then this help text is displayed.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="3e49f-134">Exemples</span><span class="sxs-lookup"><span data-stu-id="3e49f-134">Examples</span></span>  
 <span data-ttu-id="3e49f-135">Cet exemple recherche le nom de fichier du certificat avec le nom du sujet « CN=localhost » dans le magasin personnel de l'utilisateur actuel. FindPrivateKey My CurrentUser -n "CN=localhost".</span><span class="sxs-lookup"><span data-stu-id="3e49f-135">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User.FindPrivateKey My CurrentUser -n "CN=localhost".</span></span>  
  
 <span data-ttu-id="3e49f-136">Cet exemple recherche le nom de fichier du certificat avec le nom du sujet « CN=localhost » dans le magasin personnel de l'utilisateur actuel et pour sortie le chemin d'accès complet au répertoire.</span><span class="sxs-lookup"><span data-stu-id="3e49f-136">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current and output the full directory path.</span></span>  
  
```  
User.FindPrivateKey My CurrentUser -n "CN=localhost" -a  
```  
  
 <span data-ttu-id="3e49f-137">Cet exemple recherche le nom de fichier du certificat avec l'empreinte numérique « 03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52 » dans le magasin personnel de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3e49f-137">This example finds the filename of the certificate with a thumbprint of "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52", in the Personal store of the Local Computer.</span></span>  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –c  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e49f-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e49f-138">See Also</span></span>
