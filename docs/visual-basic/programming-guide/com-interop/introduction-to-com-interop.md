---
title: "Introduction to COM Interop (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "interop assemblies"
  - "COM interop, about COM interop"
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# Introduction to COM Interop (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Le modèle COM \(Component Object Model\) permet à un objet d'exposer ses fonctionnalités à d'autres composants et d'héberger des applications.  Alors que les objets COM ont été essentiels à la programmation Windows pendant de nombreuses années, les applications conçues pour le CLR \(Common Language Runtime\) offrent de nombreux avantages.  
  
 Les applications [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] remplaceront finalement celles qui ont été développées avec COM.  D'ici là, vous devrez peut\-être utiliser ou créer des objets COM à l'aide de [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)].  L'interopérabilité avec COM, ou *COM Interop*, vous permet d'utiliser des objets COM existants lors de la transition vers le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] à votre propre rythme.  
  
 L'utilisation du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] pour créer des composants COM vous permet d'utiliser COM Interop sans inscription.  Cela vous permet de contrôler quelle version de DLL est activée lorsque plusieurs versions sont installées sur un ordinateur et permet aux utilisateurs finals d'utiliser XCOPY ou FTP pour copier votre application vers un répertoire approprié sur leur ordinateur où elle peut être exécutée.  Pour plus d'informations, consultez [Registration\-Free COM Interop](../Topic/Registration-Free%20COM%20Interop.md).  
  
## Données et code managés  
 Le code développé pour le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] est appelé *code managé* et contient des métadonnées utilisées par le CLR.  Les données utilisées par les applications [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] sont appelées *données managées* car le runtime gère les tâches relatives aux données, telles que l'allocation et la libération de la mémoire, ainsi que la vérification du type.  Par défaut, [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] utilise des données et du code managés, mais vous pouvez accéder aux données et code non managés des objets COM à l'aide des assemblys d'interopérabilité \(décrits plus loin sur cette page\).  
  
## Assemblys  
 Un assembly constitue le bloc de construction principal d'une application [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)].  Il s'agit d'un ensemble de fonctionnalités qui sont générées, dotées d'une version et déployées comme une seule unité d'implémentation contenant un ou plusieurs fichiers.  Chaque assembly contient un manifeste d'assembly.  
  
## Bibliothèques de types et manifestes d'assembly  
 Les bibliothèques de types décrivent les caractéristiques des objets COM, telles que les noms des membres et les types de données.  Les manifestes d'assembly exécutent la même fonction pour les applications [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)].  Ils incluent des informations à propos des éléments suivants :  
  
-   Identité d'assembly, version, culture et signature numérique.  
  
-   Fichiers qui constituent l'implémentation de l'assembly.  
  
-   Types et ressources qui composent l'assembly.  Cela inclut les éléments qui sont exportés à partir de cet assembly.  
  
-   Dépendances de compilation des autres assemblys.  
  
-   Autorisations nécessaires au bon fonctionnement de l'assembly.  
  
 Pour plus d'informations sur les assemblys et les manifestes d'assembly, consultez [Assemblys et le Global Assembly Cache](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md).  
  
### Importation et exportation des bibliothèques de types  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] contient un utilitaire, Tlbimp, qui vous permet d'importer des informations à partir d'une bibliothèque de types vers une application [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)].  Vous pouvez générer des bibliothèques de types à partir des assemblys à l'aide de l'utilitaire Tlbexp.  
  
 Pour plus d'informations sur Tlbimp et Tlbexp, consultez [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md) et [Tlbexp.exe \(Type Library Exporter\)](../Topic/Tlbexp.exe%20\(Type%20Library%20Exporter\).md).  
  
## Assemblys d'interopérabilité  
 Les assemblys d'interopérabilité sont des assemblys [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] qui servent de pont entre le code managé et non managé, en mappant les membres de l'objet COM à des membres managés du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] équivalents.  Les assemblys d'interopérabilité créés par [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] gèrent de nombreux détails de l'utilisation d'objets COM, par exemple le marshaling d'interopérabilité.  
  
## Marshaling d'interopérabilité  
 Toutes les applications [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] partagent un ensemble de types courants qui permettent l'interopérabilité des objets, quel que soit le langage de programmation qui est utilisé.  Les paramètres et valeurs de retour des objets COM utilisent parfois des types de données différents de ceux utilisés dans du code managé.  Le *marshaling d'interopérabilité* est le processus qui consiste à empaqueter des paramètres et valeurs de retour dans des types de données équivalents lors de leurs déplacements vers et depuis des objets COM.  Pour plus d'informations, consultez [Interop Marshaling](../Topic/Interop%20Marshaling.md).  
  
## Voir aussi  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Walkthrough: Implementing Inheritance with COM Objects](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Troubleshooting Interoperability](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)   
 [Assemblys et le Global Assembly Cache](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md)   
 [Tlbexp.exe \(Type Library Exporter\)](../Topic/Tlbexp.exe%20\(Type%20Library%20Exporter\).md)   
 [Interop Marshaling](../Topic/Interop%20Marshaling.md)   
 [Registration\-Free COM Interop](../Topic/Registration-Free%20COM%20Interop.md)