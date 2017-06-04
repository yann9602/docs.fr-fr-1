---
title: "GUID_ManagedName, attribut | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: 
  - "GUID_ManagedName"
apilocation: 
  - "alink.dll"
apitype: "COM"
f1_keywords: 
  - "GUID_ManagedName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GUID_ManagedName (attribut)"
ms.assetid: 11e18095-e444-47bc-aff6-b887ac5dc01e
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# GUID_ManagedName, attribut
Définit un attribut d’interface personnalisé qui spécifie le nom de l’espace de noms managé pour une bibliothèque de composant object model \(COM\).  
  
## Syntaxe  
  
```  
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
#### Paramètres  
 `value`  
 Le nom de l’espace de noms managé pour la bibliothèque.  
  
## Définition  
 `GUID_ManagedName` est défini dans Cor.h comme suit :  
  
```  
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## Notes  
 Un attribut d’interface personnalisé définit les métadonnées pour un objet dans la bibliothèque de types.  
  
 Utilisez <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=fullName> ou <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=fullName> pour récupérer le nom managé de l’attribut.  
  
 Pour plus d’informations, consultez [Interface Attributes](../Topic/Interface%20Attributes.md) dans Visual C\+\+ documentation de référence.  
  
## Exemple  
 L’exemple suivant montre une définition de bibliothèque à l’aide de la `GUID_ManagedName` attribut.  
  
```  
[  
   ...  
   custom(GUID_ManagedName, Microsoft.VisualStudio.CommandBars.dll")  
]  
library Microsoft_VisualStudio_CommandBars  
{  
   ...  
}  
```  
  
## Configuration requise  
 **En\-tête :** Cor.h