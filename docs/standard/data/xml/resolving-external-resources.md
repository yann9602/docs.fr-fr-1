---
title: "Résolution des ressources externes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad3fa320-4b8f-4e5c-b549-01157591007a
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 824a35ee5d4ecafc45167ff3f4bc89802af4ed96
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="resolving-external-resources"></a>Résolution des ressources externes
Le **XmlResolver** propriété de la **XmlDocument** est utilisé par le **XmlDocument** classe pour localiser les ressources qui ne sont pas inline dans les données XML, telles que le type de document externe (DTD), des entités et des schémas. Ces éléments peuvent être localisés sur un réseau ou un lecteur local et sont identifiables par un URI (Uniform Resource Identifier). Cela permet la **XmlDocument** résoudre **EntityReference** nœuds qui sont présents dans le document et valider le document en fonction de la DTD ou du schéma externe.  
  
## <a name="fully-trusted-xmldocument"></a>XmlDocument d'une confiance suffisante  
 Le **XmlResolver** propriété affecte les fonctionnalités de la **XmlDocument.Load** (méthode). Le tableau ci-dessous montre comment la **XmlDocument.XmlResolver** propriété fonctionne lorsque le **XmlDocument** objet est entièrement fiable. Le tableau suivant présente la **XmlDocument.Load** méthodes lorsque l’entrée de Load est un **TextReader**, **chaîne**, **flux**, ou  **URI**. Cette table ne s’applique pas à la **charge** (méthode) si le **XmlDocument** est chargé à partir d’un **XmlReader**.  
  
|XmlResolver, propriété|Fonction|Remarques|  
|--------------------------|--------------|-----------|  
|La propriété est définie un **XmlResolver** classe qui a été créé précédemment et possède des propriétés déjà définies par l’utilisateur.|Le **XmlDocument** utilise le **XmlResolver** donné pour résoudre des noms de fichier, pour résoudre les références aux ressources externes telles que des DTD, des entités et des schémas.<br /><br /> Le **XmlResolver** est également utilisé lors de la résolution des ressources externes nécessaires lors de l’ajout ou la modification de nœuds dans le **XmlDocument**.|Le **XmlResolver** donné à la **XmlDocument** est le programme de résolution est utilisé chaque fois que des ressources ont besoin d’être localisées et résolues.|  
|La propriété est définie **null** (**rien** dans Microsoft Visual Basic .NET).|Les fonctionnalités qui nécessitent une ressource externe ne sont pas prises en charge comme la localisation d’un schéma ou DTD externe. Les entités externes ne seront pas non plus résolues et les fonctions de modification, comme l’insertion de nœuds d’entité qui demandent une résolution, ne sont pas prises en charge.|Le **XmlDocument** charge des fichiers comme étant anonymes et ne tente pas de résoudre d’autres ressources.|  
|La propriété n'est pas définie, elle reste dans son état par défaut.|Un **XmlUrlResolver** avec NULL comme valeur informations d’identification seront instanciées et utilisées par le **XmlDocument** lors de la résolution de noms de fichiers, la localisation des DTD, des entités et des schémas externes et **null** informations d’identification sont utilisées lors de la modification de nœuds.||  
  
 Le tableau suivant présente la **XmlDocument.Load** (méthode) lors de l’entrée de la **charge** est un **XmlReader** et le **XmlDocument** est niveau de confiance suffisant.  
  
|XmlResolver, propriété|Fonction|Remarques|  
|--------------------------|--------------|-----------|  
|Le **XmlResolver** classe utilisée par le **XmlDocument** est la même classe utilisée par le **XmlReader**.|Le **XmlDocument** utilise le **XmlResolver** qui a été assigné à la **XmlReader**.<br /><br /> Le **XmlDocument.Resolver** propriété ne peut pas être définie, quel que soit le **XmlDocument** niveau de confiance, car elle reçoit un **XmlResolver** à partir de la  **XmlReader**. Vous ne pouvez pas essayer de remplacer les paramètres de la **XmlResolver**' **XmlResolver** en définissant le **XmlResolver** propriété de la **XmlDocument**.|Le **XmlReader** peut être le **XmlTextReader**, **XmlValidatingReader**, ou un lecteur à l’écriture personnalisée. Si le lecteur utilisé prend en charge la résolution d’entité, les entités externes sont résolues. Si le lecteur passé ne prend pas en charge les références d'entité, dans ce cas celles-ci ne sont pas résolues.|  
  
## <a name="semi-trusted-xmldocument"></a>XmlDocument d'une confiance partielle  
 Le tableau suivant montre comment la **XmlDocument.XmlResolver** propriété fonctionne lorsque l’objet est le niveau de confiance partiel. Ce tableau s’applique à la **XmlDocument.Load** méthodes lorsque l’entrée de Load est un **TextReader**, **chaîne**, **flux**, ou  **URI**. Cette table ne s’applique pas à la **charge** (méthode) si le **XmlDocument** est chargé à partir d’un **XmlReader**.  
  
|XmlResolver, propriété|Fonction|Remarques|  
|--------------------------|--------------|-----------|  
|Dans le scénario de niveau de confiance partiel, le **XmlResolver** propriété ne peut pas être définie sur une autre que null.|Un **XmlUrlResolver** avec **null** informations d’identification seront instanciées et utilisées par le **XmlDocument** lors de la résolution de noms de fichiers, la localisation des DTD externes, entités, et schémas, et **null** informations d’identification sont utilisées lors de la modification de nœuds.|Ce comportement est identique au comportement lorsque le **XmlResolver** propriété n’est pas définie, elle reste dans son état par défaut.<br /><br /> Le **XmlDocument** utilise des autorisations anonymes pour toutes les actions.|  
|La propriété est définie **null** (**rien** dans Microsoft Visual Basic .NET).|Aucune fonctionnalité qui nécessite une ressource externe n’est prise en charge comme la localisation d’un schéma ou DTD externe. Les entités externes ne seront pas non plus résolues et les fonctions de modification, comme l’insertion de nœuds d’entité qui demandent une résolution, ne sont pas prises en charge.|Lorsque la propriété est **null**, le comportement est le même, que la **XmlDocument** est entièrement confiance partiel ou suffisant.|  
|La propriété n'est pas définie, elle reste dans son état par défaut.|Un **XmlUrlResolver** avec **null** informations d’identification seront instanciées et utilisées par le **XmlDocument** lors de la résolution de noms de fichiers, la localisation des DTD externes, entités, et schémas, et **null** informations d’identification sont utilisées lors de la modification de nœuds.|Le **XmlDocument** utilise des autorisations anonymes pour toutes les actions.|  
  
 Ce tableau s’applique à la **XmlDocument.Load** (méthode) lors de l’entrée de la **charge** est un **XmlReader**et le **XmlDocument** est niveau de confiance partiel.  
  
|XmlResolver, propriété|Fonction|Remarques|  
|--------------------------|--------------|-----------|  
|Le **XmlResolver** classe utilisée par le **XmlDocument** est identique à celui utilisé par le **XmlReader**.|Le **XmlDocument** utilise le **XmlResolver** qui a été assigné à la **XmlReader**.<br /><br /> Le **XmlDocument.Resolver** propriété ne peut pas être définie, quel que soit le **XmlDocument** niveau de confiance, car elle reçoit un **XmlResolver** à partir de la  **XmlReader**. Vous ne pouvez pas essayer de remplacer les paramètres de la **XmlResolver** **XmlResolver** en définissant le **XmlResolver** propriété de la **XmlDocument**.|Le **XmlReader** peut être le **XmlTextReader**, validation <xref:System.Xml.XmlReader>, ou un lecteur à l’écriture personnalisée. Si le lecteur utilisé prend en charge la résolution d’entité, les entités externes sont résolues. Si le lecteur passé ne prend pas en charge de références d'entité, dans ce cas celles-ci ne sont pas résolues.|  
  
 Le paramétrage de XmlResolver pour contenir les informations d'identification correctes permet d'accéder à des ressources externes.  
  
> [!NOTE]
>  Il n’existe aucun moyen de récupérer le **XmlResolver** propriété. Cela permet d’empêcher un utilisateur de réutiliser une **XmlResolver** sur les informations d’identification ont été définies. En outre, si un **XmlTextReader** ou de la validation <xref:System.Xml.XmlReader> est utilisée pour charger le **XmlDocument** et le **XmlDocument** a un programme de résolution a été défini, les programmes de résolution à partir de ces lecteurs ne sont pas mis en cache par le **XmlDocument** après le **charge** phase, dans la mesure où cela présente également un risque de sécurité.  
  
 Pour plus d'informations, consultez la section Notes de la page de référence <xref:System.Xml.XmlResolver>.  
  
## <a name="see-also"></a>Voir aussi  
 [Document Object Model (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
