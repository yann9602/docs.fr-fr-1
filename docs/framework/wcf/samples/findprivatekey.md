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
# <a name="findprivatekey"></a>FindPrivateKey
Il peut être difficile de rechercher l'emplacement et le nom du fichier de clé privée associé à un certificat X.509 spécifique dans le magasin de certificats. L'outil FindPrivateKey.exe facilite ce processus.  
  
> [!IMPORTANT]
>  FindPrivateKey est un exemple qui doit être compilé avant son utilisation. Consultez la section « pour générer le projet FindPrivateKey » ci-dessous pour obtenir des instructions sur la création de l’outil FindPrivateKey.  
  
 Les certificats X.509 sont installés par un administrateur ou tout utilisateur sur l'ordinateur. Cependant, le certificat peut être consulté par un service qui s'exécute sous un compte différent (par exemple, le compte ASPNET sur [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ou le compte SERVICE RÉSEAU sur [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]).  
  
 Ce compte peut ne pas avoir accès au fichier de clé privée parce qu'il n'a pas installé le certificat à l'origine. L'outil FindPrivateKey vous donne l'emplacement du fichier de clé privée d'un certificat X.509 donné. Vous pouvez ajouter ou supprimer des autorisations à ce fichier une fois que vous connaissez l'emplacement du fichier de clé privée des certificats X.509 particuliers.  
  
 Les exemples qui utilisent des certificats pour la sécurité utilisent l'outil FindPrivateKey dans le fichier Setup.bat. Une fois que le fichier de clé privée a été trouvé, vous pouvez utiliser des autres outils tels que Cacls.exe pour définir les droits d'accès appropriés sur le fichier.  
  
 Lors de l'exécution d'un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sous un compte d'utilisateur, tel qu'un fichier exécutable auto-hébergé, vérifiez que le compte d'utilisateur dispose d'un accès en lecture seule au fichier. Lors de l'exécution d'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sous IIS (Internet Information Services), les comptes par défaut sous lesquels le service s'exécute sont ASPNET sur [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ou SERVICE RESEAU sur [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] qui, par défaut, n'ont pas accès au fichier de clé privée.  
  
## <a name="examples"></a>Exemples  
 Lorsque vous accédez à un certificat pour lequel le processus n'a pas de privilège d'accès en lecture, vous voyez un message d'exception semblable à l'exemple suivant.  
  
```  
System.ArgumentException was unhandled  
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."  
Source="System.ServiceModel"  
```  
  
 Lorsque cela se produit, utilisez l'outil FindPrivateKey pour rechercher le fichier de clé privée, puis définissez le droit d'accès pour le processus sous lequel le service s'exécute. Cela peut être fait avec l'outil Cacls.exe, comme le montre l'exemple suivant.  
  
```  
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
```  
  
#### <a name="to-build-the-findprivatekey-project"></a>Pour générer le projet FindPrivateKey  
  
1.  Ouvrez l'[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] et sélectionnez le sous-répertoire spécifique à une langue se trouvant sous l'emplacement d'installation de l'exemple.  
  
2.  Double-cliquez sur l'icône du fichier .sln pour ouvrir ce dernier dans Visual Studio.  
  
3.  Dans le **générer** menu, sélectionnez **régénérer la Solution**. Les fichiers de programme du client sont générés dans client\bin, et les fichiers de programme du service sont générés dans service\bin.  
  
4.  La génération de la solution génère le fichier : FindPrivateKey.exe.  
  
## <a name="conventionscommand-line-entries"></a>Entrées de lignes de commande - Conventions  
 « [*option*] » représente un ensemble facultatif de paramètres.  
  
 « {*option*} » représente un jeu obligatoire de paramètres.  
  
 «*option1* &#124; *option2*« représente un choix entre des ensembles d’options.  
  
 «\<*valeur*> » représente une valeur de paramètre doit être entré.  
  
## <a name="usage"></a>Utilisation  
  
```  
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]  
```  
  
 Où :  
  
```  
       <subjectName> The subject name of the certificate  
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)  
       -f            output file name only  
       -d            output directory only  
       -a            output absolute file name  
```  
  
 Si aucun paramètre n'est spécifié à l'invite de commandes, ce texte d'aide s'affiche.  
  
## <a name="examples"></a>Exemples  
 Cet exemple recherche le nom de fichier du certificat avec le nom du sujet « CN=localhost » dans le magasin personnel de l'utilisateur actuel. FindPrivateKey My CurrentUser -n "CN=localhost".  
  
 Cet exemple recherche le nom de fichier du certificat avec le nom du sujet « CN=localhost » dans le magasin personnel de l'utilisateur actuel et pour sortie le chemin d'accès complet au répertoire.  
  
```  
User.FindPrivateKey My CurrentUser -n "CN=localhost" -a  
```  
  
 Cet exemple recherche le nom de fichier du certificat avec l'empreinte numérique « 03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52 » dans le magasin personnel de l'ordinateur local.  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –c  
```  
  
## <a name="see-also"></a>Voir aussi
