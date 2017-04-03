---
title: "Interopérabilité (Guide de programmation C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
caps.latest.revision: 31
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d4fb156e095d4cec9a0e690a516414282359356a
ms.lasthandoff: 03/13/2017

---
# <a name="interoperability-c-programming-guide"></a>Interopérabilité (Guide de programmation C#)
L’interopérabilité vous permet de préserver et de tirer parti d’investissements existants en code non managé. Le code qui s’exécute sous le contrôle du common language runtime (CLR) est appelé *code managé*, et le code qui s’exécute en dehors du CLR est appelé *code non managé*. COM, COM+, les composants C++, les composants ActiveX et l’API Microsoft Win32 sont des exemples de code non managé.  
  
 Le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] permet l’interopérabilité avec du code non managé par des services d’appel de code non managé, l’espace de noms <xref:System.Runtime.InteropServices>, l’interopérabilité C++ et l’interopérabilité COM (COM Interop).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble de l’interopérabilité](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 Décrit les méthodes qui permettent l’interopérabilité entre le code managé et le code non managé en C#.  
  
 [Comment : accéder aux objets Office Interop à l’aide des fonctionnalités Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 Décrit les fonctionnalités introduites dans Visual C# 2010 pour faciliter la programmation Office.  
  
 [Comment : utiliser des propriétés indexées dans la programmation COM Interop](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 Explique comment utiliser des propriétés indexées pour accéder aux propriétés COM qui ont des paramètres.  
  
 [Comment : utiliser l’appel de code non managé pour lire un fichier audio](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 Explique comment utiliser des services d’appel de code non managé pour lire un fichier son .wav sur le système d’exploitation Windows.  
  
 [Procédure pas à pas : programmation Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 Montre comment créer un classeur Excel et un document Word qui contient un lien vers le classeur.  
  
 [Exemple de classe COM](../../../csharp/programming-guide/interop/example-com-class.md)  
 Montre comment exposer une classe C# en tant qu’objet COM.  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=fullName>   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Interopération avec du code non managé](https://msdn.microsoft.com/library/sd10k43k)   
 [Procédure pas à pas : programmation Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
