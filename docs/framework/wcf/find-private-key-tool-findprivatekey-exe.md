---
title: "Outil de recherche de clé privée (FindPrivateKey.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5e2110e129b293ffb04c8e3eb69a5c3bfe83c17b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="find-private-key-tool-findprivatekeyexe"></a>Outil de recherche de clé privée (FindPrivateKey.exe)
Cet outil de ligne de commande peut être utilisé pour récupérer une clé privée provenant d'un magasin de certificats. Par exemple, FindPrivateKey.exe peut être utilisé pour rechercher l'emplacement et le nom du fichier de clé privée associé à un certificat X.509 spécifique dans le magasin de certificats.  
  
> [!IMPORTANT]
>  L'outil FindPrivateKey est fourni à titre d'exemple WCF. Pour plus d'informations sur l'emplacement de l'exemple et comment le générer, consultez  
  
## <a name="syntax"></a>Syntaxe  
  
```  
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]  
```  
  
## <a name="remarks"></a>Remarques  
 Les tables suivantes décrivent les arguments et les options qui peuvent être utilisés avec l’outil de recherche de clé privée Clé (FindPrivateKey.exe).  
  
|Argument|Description|  
|--------------|-----------------|  
|`storeName`|Nom du magasin de certificats|  
|`storeLocation`|Emplacement du magasin de certificats|  
  
|Option|Description|  
|------------|-----------------|  
|`/n <`*subjectName*`>`|Spécifie le nom du sujet du certificat.|  
|`/t <`*l’empreinte numérique*`>`|Spécifie l'empreinte numérique du certificat. Utilisez Certmgr.exe pour récupérer l'empreinte numérique du certificat.|  
|`/f`|Affiche le nom de fichier uniquement.|  
|`/d`|Affiche le répertoire uniquement.|  
|`/a`|Affiche le nom de fichier absolu.|  
  
## <a name="examples"></a>Exemples  
 La commande suivante permet de récupérer la clé privée associée à John Doe.  
  
```  
FindPrivateKey My CurrentUser -n "CN=John Doe"  
```  
  
 La commande suivante permet de récupérer la clé privée associée à l'ordinateur local.  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a  
```
