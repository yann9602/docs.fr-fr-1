---
title: "WCF et IDN (Internationalized Domain Names) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# WCF et IDN (Internationalized Domain Names)
La prise en charge a été ajoutée pour tenir compte des services WCF avec des noms IDN \(Internationalized Domain Names\).  Un nom de domaine international est un nom de domaine qui contient des caractères non ASCII.  Cette prise en charge inclut la capacité d'héberger un service WCF avec un nom IDN et un client WCF pour parler à un service Web avec un nom IDN.  
  
## System.Uri et IDN  
 <xref:System.Uri> contient deux propriétés : <xref:System.Uri.Host%2A> et <xref:System.Uri.DnsSafeHost%2A>.  Ces propriétés contiennent des valeurs Unicode ou Punycode en fonction des paramètres de configuration pour IDN.  
  
 L'IDN est activé dans le fichier de configuration d'une application à l'aide du XML suivant  
  
```  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
  
```  
  
 L'élément \<idn\> contient l'attribut activé qui peut être défini sur l'une des valeurs suivantes :  
  
1.  « None »  
  
2.  « AllExceptIntranet »  
  
3.  « All »  
  
 Lorsque le paramètre IDN a la valeur « None », aucune conversion n'est exécutée par Uri.Host ou Uri.DnsSafeHost.  Lorsque le paramètre IDN a la valeur « All », uri.Host reste Unicode et uri.DnsSafeHost est converti en Punycode.  Lorsque le paramètre IDN a la valeur « AllExceptIntranet », uri.DnsSafeHost est converti en Punycode pour les adresses Internet, et reste Unicode pour les adresses intranet.  Ce paramètre est important pour la résolution de noms DNS correcte.  Notez qu'il n'est pas nécessaire de configurer ce paramètres pour Windows 8 et les versions plus récentes.  
  
> [!WARNING]
>  Vous ne devez jamais coder une adresse en dur à l'aide de Punycode.  WCF le convertit pour vous en fonction des paramètres de configuration que vous appliquez.  
  
> [!WARNING]
>  Lorsque vous ajoutez des caractères Unicode à applicationHost.exe.config, enregistrez le fichier à l'aide de l'encodage UTF\-8.  
  
## Voir aussi  
 [System.Uri](http://msdn.microsoft.com/library/system.uri.aspx)