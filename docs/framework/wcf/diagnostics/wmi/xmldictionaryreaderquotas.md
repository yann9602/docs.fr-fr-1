---
title: XmlDictionaryReaderQuotas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 980a7eacd095dc1b601d63f5a807f2e287c09885
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas
XmlDictionaryReaderQuotas  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class XmlDictionaryReaderQuotas  
{  
  sint32 MaxArrayLength;  
  sint32 MaxBytesPerRead;  
  sint32 MaxDepth;  
  sint32 MaxNameTableCharCount;  
  sint32 MaxStringContentLength;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe XmlDictionaryReaderQuotas ne définit aucune méthode.  
  
## <a name="properties"></a>Propriétés  
 La classe XmlDictionaryReaderQuotas a les propriétés suivantes :  
  
### <a name="maxarraylength"></a>MaxArrayLength  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 La longueur de tableau maximale autorisée.  
  
### <a name="maxbytesperread"></a>MaxBytesPerRead  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Le nombre maximal d'octets autorisés retournés pour chaque lecture.  
  
### <a name="maxdepth"></a>MaxDepth  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Profondeur maximale de nœud imbriqué par lecture.  
  
### <a name="maxnametablecharcount"></a>MaxNameTableCharCount  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Le nombre maximal de caractères autorisés dans un nom de table.  
  
### <a name="maxstringcontentlength"></a>MaxStringContentLength  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre maximal de caractères autorisés dans un contenu d'élément XML.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
