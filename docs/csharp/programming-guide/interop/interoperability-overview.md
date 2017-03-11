---
title: "Vue d&#39;ensemble de l&#39;interop&#233;rabilit&#233; (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "langage C#, interopérabilité"
  - "interopérabilité C++"
  - "COM Interop"
  - "interopérabilité, à propos de l'interopérabilité"
  - "appel de code non managé"
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
caps.latest.revision: 43
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 43
---
# Vue d&#39;ensemble de l&#39;interop&#233;rabilit&#233; (Guide de programmation C#)
Cette rubrique décrit les méthodes qui permettent d'activer l'interopérabilité entre le code managé et le code non managé C\#.  
  
## Appel de code non managé  
 L'*appel de code non managé* est un service qui permet à du code managé d'appeler des fonctions non managées implémentées dans des bibliothèques de liens dynamiques \(DLL\), comme celles figurant dans l'interface Microsoft API Win32.  Elle localise et appelle une fonction exportée et marshale ses arguments \(entiers, chaînes, tableaux, structures\) sur les limites d'interopérabilité si nécessaire.  
  
 Pour plus d'informations, consultez [Consuming Unmanaged DLL Functions](../Topic/Consuming%20Unmanaged%20DLL%20Functions.md) et [Comment : utiliser l'appel de code non managé pour lire un fichier audio](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md).  
  
> [!NOTE]
>  Le [Common Language Runtime](../Topic/Common%20Language%20Runtime%20\(CLR\).md) \(CLR\) gère l'accès aux ressources système.  L'appel de code non managé en dehors du CLR permet de passer outre le mécanisme de sécurité et présente par conséquent un risque de sécurité.  Par exemple, le code non managé peut appeler directement des ressources dans le code non managé en contournant les mécanismes de sécurité du CLR.  Pour plus d'informations, consultez [.NET Framework Security](http://go.microsoft.com/fwlink/?LinkId=37122).  
  
## C\+\+ Interop  
 Vous pouvez recourir à l'interopérabilité C\+\+, également connue sous le nom « It Just Works » \(IJW\), pour encapsuler une classe C\+\+ native et pouvoir l'utiliser dans du code créé en C\# ou dans un autre langage .NET Framework.  Pour cela, vous devez écrire un code C\+\+ pour encapsuler un composant DLL ou COM natif.  Contrairement à d'autres langages .NET Framework, [!INCLUDE[vcprvc](../../../csharp/programming-guide/interop/includes/vcprvc-md.md)] offre une prise en charge de l'interopérabilité qui autorise la présence de code managé et non managé dans la même application, voire même dans le même fichier.  Vous pouvez ensuite générer le code C\+\+ à l'aide du commutateur **\/clr** du compilateur pour créer un assembly managé.  Il vous suffit enfin d'ajouter une référence à l'assembly dans votre projet C\# et d'utiliser les objets encapsulés de la même manière que vous utiliseriez d'autres classes managées.  
  
## Exposition de composants COM à C\#  
 Vous pouvez exploiter un composant COM à partir d'un projet C\#.  La procédure généralement employée est la suivante :  
  
1.  Recherchez un composant COM à utiliser et inscrivez\-le.  Utilisez regsvr32.exe pour inscrire une DLL COM ou annuler son inscription.  
  
2.  Ajoutez une référence au composant COM ou à une bibliothèque de types dans votre projet.  
  
     Au moment où vous ajoutez la référence, [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] utilise l'outil [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md) qui utilise une bibliothèque de types comme entrée pour produire en sortie un assembly d'interopérabilité .NET Framework.  L'assembly, également nommé wrapper RCW \(Runtime Callable Wrapper\), contient les classes et interfaces managées qui encapsulent les classes et interfaces COM qui se trouvent dans la bibliothèque de types.  [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] ajoute au projet une référence à l'assembly généré.  
  
3.  Créez une instance d'une classe définie dans le wrapper RCW.  Cette étape crée à son tour une instance de l'objet COM.  
  
4.  Utilisez l'objet comme vous utiliseriez simplement d'autres objets managés.  Dès que l'objet est récupéré par l'opération garbage collection, l'instance de l'objet COM est également libérée de la mémoire.  
  
 Pour plus d'informations, consultez [Exposing COM Components to the .NET Framework](../Topic/Exposing%20COM%20Components%20to%20the%20.NET%20Framework.md).  
  
## Exposition de C\# à COM  
 Les clients COM peuvent exploiter des types C\# qui ont été exposés en bonne et due forme.  Les étapes de base pour l'exposition des types C\# sont les suivantes :  
  
1.  Ajoutez des attributs d'interopérabilité au projet C\#.  
  
     Vous pouvez rendre un assembly COM visible en modifiant les propriétés du projet [!INCLUDE[csprcs](../../../csharp/includes/csprcs-md.md)].  Pour plus d'informations, consultez [Informations de l'assembly, boîte de dialogue](/visual-studio/ide/reference/assembly-information-dialog-box).  
  
2.  Créez une bibliothèque de types COM et inscrivez\-la pour l'utilisation de COM.  
  
     Vous pouvez modifier les propriétés de projet [!INCLUDE[csprcs](../../../csharp/includes/csprcs-md.md)] pour enregistrer automatiquement l'assembly C\# pour COM Interop.  [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] utilise [Regasm.exe \(Assembly Registration Tool\)](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md), à l'aide du commutateur de ligne de commande `/tlb`, qui prend un assembly managé comme entrée, pour générer une bibliothèque de types.  La bibliothèque de types créée décrit les types `public` dans l'assembly et ajoute des entrées du Registre afin que les clients COM puissent créer des classes managées.  
  
 Pour plus d'informations, consultez [Exposing .NET Framework Components to COM](../Topic/Exposing%20.NET%20Framework%20Components%20to%20COM.md) et [Exemple de classe COM](../../../csharp/programming-guide/interop/example-com-class.md).  
  
## Voir aussi  
 [Improving Interop Performance](http://go.microsoft.com/fwlink/?LinkId=99564)   
 [Introduction to COM Interop](http://go.microsoft.com/fwlink/?LinkId=112406)   
 [Marshaling between Managed and Unmanaged Code](http://go.microsoft.com/fwlink/?LinkId=112398)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Advanced COM Interoperability](http://msdn.microsoft.com/fr-fr/3ada36e5-2390-4d70-b490-6ad8de92f2fb)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)