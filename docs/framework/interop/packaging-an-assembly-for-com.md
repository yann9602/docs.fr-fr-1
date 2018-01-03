---
title: Empaquetage d'un assembly pour COM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, packaging assemblies
- packaging assemblies for COM
- Tlbexp.exe
- TypeLibConverter class
- .NET Services Installation tool
- Assembly Registration tool
- Type Library Exporter
- Reqsvcs.exe
- interoperation with unmanaged code, exposing .NET Framework components
- interoperation with unmanaged code, packaging assemblies
- COM interop, exposing COM components
- Reqasm.exe
ms.assetid: 39dc55aa-f2a1-4093-87bb-f1c0edb6e761
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72b9237a8abeee936070799c5087abc6b45ff3b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="packaging-an-assembly-for-com"></a>Empaquetage d'un assembly pour COM
Les développeurs COM peuvent tirer parti des informations suivantes sur les types managés qu’ils prévoient d’incorporer dans leur application :  
  
-   Une liste des types que les applications COM peuvent consommer  
  
     Certains types managés ne sont pas visibles par COM, certains sont visibles mais ne peuvent pas être créés, et certains sont visibles et peuvent être créés. Un assembly peut comprendre tout combinaison de types invisibles, visibles, ne pouvant pas être créés et pouvant être créés. Par souci d’exhaustivité, identifiez les types dans un assembly que vous prévoyez d’exposer à COM, en particulier quand ces types sont un sous-ensemble des types exposés au .NET Framework.  
  
     Pour plus d’informations, consultez [Qualification des types .NET en vue d’une interopérabilité](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).  
  
-   Instructions de gestion de version  
  
     Les classes managées qui implémentent l’interface de classe (une interface COM générée par interop) sont soumises aux restrictions de gestion de version.  
  
     Pour connaître les instructions sur l’utilisation de l’interface de classe, consultez [Présentation de l’interface de classe](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024).  
  
-   Instructions de déploiement  
  
     Les assemblys avec nom fort signés par un serveur de publication peuvent être installés dans le global assembly cache. Les assemblys non signés doivent être installés sur l’ordinateur de l’utilisateur en tant qu’assemblys privés.  
  
     Pour plus d’informations, consultez [Aspects de la sécurité des assemblys](../../../docs/framework/app-domains/assembly-security-considerations.md).  
  
-   Inclusion de bibliothèque de types  
  
     La plupart des types nécessitent une bibliothèque de types en cas de consommation par une application COM. Vous pouvez générer une bibliothèque de types ou demander aux développeurs COM d’effectuer cette tâche. Le [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] fournit les options suivantes pour générer une bibliothèque de types :  
  
    -   [Exportateur de bibliothèques de types](#cpconpackagingassemblyforcomanchor1)  
  
    -   [Classe TypeLibConverter](#cpconpackagingassemblyforcomanchor2)  
  
    -   [Outil Assembly Registration](#cpconpackagingassemblyforcomanchor3)  
  
    -   [Outil .NET Services Installation](#cpconpackagingassemblyforcomanchor4)  
  
     Quel que soit le mécanisme que vous choisissez, seuls les types publics définis dans l’assembly que vous fournissez sont inclus dans la bibliothèque de types générée.  
  
     Vous pouvez empaqueter une bibliothèque de types dans un fichier séparé ou l’incorporer en tant que fichier de ressources Win32 dans une application .NET. Microsoft Visual Basic 6.0 effectuait automatiquement cette tâche pour vous, mais quand vous utilisez [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] vous devez incorporer votre bibliothèque de types manuellement. Pour obtenir des instructions, consultez [Guide pratique pour incorporer des bibliothèques de types comme des ressources Win32 dans les applications](http://msdn.microsoft.com/en-us/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44).  
  
<a name="cpconpackagingassemblyforcomanchor1"></a>   
## <a name="type-library-exporter"></a>Exportateur de bibliothèques de types  
 L’outil en ligne de commande [Exporter.exe (exportateur de bibliothèques de types)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) permet de convertir les classes et les interfaces contenues dans un assembly en une bibliothèque de types COM. Une fois les informations de type de la classe disponibles, les clients COM peuvent créer une instance de la classe .NET et appeler les méthodes de l’instance comme s’il s’agissait d’un objet COM. Tlbexp.exe convertit un assembly entier à la fois. Vous ne pouvez pas utiliser Tlbexp.exe pour générer des informations sur les types pour un sous-ensemble de types définis dans un assembly.  
  
<a name="cpconpackagingassemblyforcomanchor2"></a>   
## <a name="typelibconverter-class"></a>Classe TypeLibConverter  
 La classe <xref:System.Runtime.InteropServices.TypeLibConverter>, qui se trouve dans l’espace de noms **System.Runtime.Interop**, convertit les classes et interfaces contenues dans un assembly en une bibliothèque de types COM. Cette API produit les mêmes informations de type que l’outil Type Library Exporter décrit dans la section précédente.  
  
 La **classe TypeLibConverter** implémente le <xref:System.Runtime.InteropServices.ITypeLibConverter>.  
  
<a name="cpconpackagingassemblyforcomanchor3"></a>   
## <a name="assembly-registration-tool"></a>Outil Assembly Registration Tool  
 L’[outil Assembly Registration Tool (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) peut générer et inscrire une bibliothèque de types quand vous appliquez l’option **/tlb:**. Les clients COM exigent que les bibliothèques de types soient installées dans le Registre de Windows. Sans cette option, Regasm.exe inscrit uniquement les types dans un assembly, pas la bibliothèque de types. Inscrire les types dans un assembly et inscrire la bibliothèque de types sont deux activités distinctes.  
  
<a name="cpconpackagingassemblyforcomanchor4"></a>   
## <a name="net-services-installation-tool"></a>Outil .NET Services Installation  
 L’[Outil .NET Services Installation (Regsvcs.exe)](../../../docs/framework/tools/regsvcs-exe-net-services-installation-tool.md) ajoute des classes managées aux Services de composants Windows 2000 et combine plusieurs tâches dans un seul outil. En plus de charger et d’inscrire un assembly, Regsvcs.exe peut générer, inscrire et installer la bibliothèque de types dans une application COM+ 1.0 existante.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.InteropServices.TypeLibConverter>  
 <xref:System.Runtime.InteropServices.ITypeLibConverter>  
 [Exposition de composants .NET Framework à COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Qualifier des types .NET pour l'interopérabilité](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md)  
 [Présentation de l’Interface de classe](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024)  
 [Aspects de la sécurité des assemblys](../../../docs/framework/app-domains/assembly-security-considerations.md)  
 [Tlbexp.exe (exportateur de bibliothèques de types)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)  
 [Inscription d’assemblys dans COM](../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [Guide pratique pour incorporer des bibliothèques de types comme des ressources Win32 dans les applications](http://msdn.microsoft.com/en-us/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44)
