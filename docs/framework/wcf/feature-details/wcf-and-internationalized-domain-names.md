---
title: WCF et IDN (Internationalized Domain Names)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cae287ab440115b15f6c26209a3d40bee4f9703b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-and-internationalized-domain-names"></a>WCF et IDN (Internationalized Domain Names)
La prise en charge a été ajoutée pour tenir compte des services WCF avec des noms IDN (Internationalized Domain Names). Un nom de domaine international est un nom de domaine qui contient des caractères non ASCII. Cette prise en charge inclut la capacité d'héberger un service WCF avec un nom IDN et un client WCF pour parler à un service Web avec un nom IDN.  
  
## <a name="systemuri-and-idn"></a>System.Uri et IDN  
 <xref:System.Uri> contient deux propriétés : <xref:System.Uri.Host%2A> et <xref:System.Uri.DnsSafeHost%2A>. Ces propriétés contiennent des valeurs Unicode ou Punycode en fonction des paramètres de configuration pour IDN.  
  
 L'IDN est activé dans le fichier de configuration d'une application à l'aide du XML suivant  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
```  
  
 Le \<idn > élément contient l’attribut activé qui peut être définie à une des valeurs suivantes :  
  
1.  « None »  
  
2.  « AllExceptIntranet »  
  
3.  « Tous »  
  
 Lorsque le paramètre IDN a la valeur « None », aucune conversion est effectuée par Uri.Host ou Uri.DnsSafeHost. Lorsque le paramètre IDN a la valeur « Tous », uri. Hôte reste Unicode et l’uri. DnsSafeHost est converti en Punycode. Lorsque le paramètre IDN a la valeur « AllExceptIntranet », les uri. DnsSafeHost est converti en Punycode pour les adresses internet et reste Unicode pour les adresses intranet. Ce paramètre est important pour la résolution de noms DNS correcte. Notez qu'il n'est pas nécessaire de configurer ce paramètres pour Windows 8 et les versions plus récentes.  
  
> [!WARNING]
>  Vous ne devez jamais coder une adresse en dur à l'aide de Punycode. WCF le convertit pour vous en fonction des paramètres de configuration que vous appliquez.  
  
> [!WARNING]
>  Lorsque vous ajoutez des caractères Unicode à applicationHost.exe.config, enregistrez le fichier à l'aide de l'encodage UTF-8.  
  
## <a name="see-also"></a>Voir aussi  
 [System.Uri](http://msdn.microsoft.com/library/system.uri.aspx)
