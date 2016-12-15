---
title: "Introduction to the C# Language and the .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# language, about C# language"
  - "Visual C#, about"
ms.assetid: 0a2dff4e-cd84-42ff-8141-e89889b24081
caps.latest.revision: 32
caps.handback.revision: 32
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Introduction to the C# Language and the .NET Framework
[!INCLUDE[vs2017banner](../../csharp/includes/vs2017banner.md)]

C\# est un langage orienté objet de type sécurisé et élégant qui permet aux développeurs de générer diverses applications sécurisées et fiables qui s'exécutent sur le [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)].  Vous pouvez utiliser le langage C\# pour créer entre autres des applications clientes Windows, des services Web XML, des composants distribués, des applications client\-serveur et des applications de base de données.  Visual C\# fournit un éditeur de code avancé, des concepteurs d'interfaces utilisateur pratiques, un débogueur intégré et de nombreux autres outils pour faciliter le développement d'applications basées sur le langage C\# et [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)].  
  
> [!NOTE]
>  La documentation de [!INCLUDE[csprcs](../../csharp/includes/csprcs_md.md)] suppose que vous possédez des connaissances de base sur les concepts de programmation.  Si vous êtes débutant complet, il peut être utile d'explorer [!INCLUDE[csprcsxpr](../../csharp/getting-started/includes/csprcsxpr_md.md)], disponible sur le Web.  Vous pouvez également tirer parti de carnets et ressources Web à propos de C\# pour acquérir des compétences de programmation pratiques.  
  
## Langage C\#  
 La syntaxe C\# est très expressive, mais elle est également simple et facile à apprendre.  La syntaxe de C\# est facile à reconnaître à ses accolades si vous connaissez déjà les langages C, C\+\+ ou Java.  Si vous connaissez déjà l'un de ces langages, vous pouvez devenir très vite productif en C\#.  La syntaxe C\# permet de répondre à de nombreuses complexités de C\+\+ en fournissant des fonctionnalités puissantes telles que des types valeur Nullable, des énumérations, des délégués, des expressions lambda et des accès directs à la mémoire qui n'existent pas en Java.  C\# prend en charge des méthodes et types génériques qui améliorent la cohérence et les performances des types, ainsi que des itérateurs, qui permettent aux implémenteurs de classes de collection de définir des comportements d'itération personnalisés simples à utiliser par le code client.  Les expressions [!INCLUDE[vbteclinqext](../../csharp/getting-started/includes/vbteclinqext_md.md)] transforment les requêtes fortement typées en construction de langage de premier ordre.  
  
 En tant que langage orienté objet, C\# prend en charge les concepts d'encapsulation, d'héritage et de polymorphisme.  Toutes les variables et méthodes, y compris la méthode `Main`, point d'entrée de l'application, sont encapsulées dans des définitions de classe.  Une classe peut hériter directement d'une classe parente, mais elle peut implémenter un nombre quelconque d'interfaces.  Les méthodes qui substituent des méthodes virtuelles dans une classe parente requièrent le mot clé `override`, ce qui évite toute redéfinition accidentelle.  En C\#, le type struct ressemble à une classe légère ; alloué par pile, il peut implémenter des interfaces mais ne prend pas l'héritage en charge.  
  
 Outre ces principes orientés objet de base, C\# permet de développer facilement des composants logiciel à travers plusieurs constructions de langage innovatrices, y compris les éléments suivants :  
  
-   Les signatures de méthodes encapsulées, appelées *délégués*, qui activent les notifications d'événement de type sécurisé.  
  
-   Les propriétés, utilisées comme accesseurs pour les variables membres privés.  
  
-   Les attributs, qui fournissent des métadonnées déclaratives à propos des types au moment de l'exécution.  
  
-   Les commentaires de la documentation XML inline.  
  
-   [!INCLUDE[vbteclinqext](../../csharp/getting-started/includes/vbteclinqext_md.md)] qui fournit des fonctions de requête intégrées à travers diverses sources de données.  
  
 Si vous devez interagir avec d'autres logiciels Windows tels que des objets COM ou des DLL Win32 natives, vous pouvez le faire en C\# à l'aide d'un processus appelé « interopérabilité ». L'interopérabilité offre aux programmes C\# autant de possibilités qu'une application C\+\+ native.  C\# prend en charge les pointeurs et le concept de code « unsafe » lorsque l'accès direct à la mémoire est absolument essentiel.  
  
 En C\#, le processus de génération est plus simple qu'en C et C\+\+ et plus souple qu'en Java.  Il n'y a pas de fichiers d'en\-tête séparés et les méthodes et types peuvent être déclarés dans n'importe quel ordre.  Un fichier source C\# peut définir tout nombre de classes, structures, interfaces et événements.  
  
 Voici quelques ressources C\# supplémentaires :  
  
-   Vous trouverez une bonne présentation générale du langage dans le chapitre 1 de [Spécification du langage C\#](../../csharp/language-reference/language-specification.md).  
  
-   Pour plus d'informations sur des aspects spécifiques du langage C\#, consultez [Référence C\#](../../csharp/language-reference/index.md).  
  
-   Pour plus d'informations sur [!INCLUDE[vbteclinq](../../csharp/includes/vbteclinq_md.md)], consultez [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md).  
  
-   Pour accéder aux ressources et articles les plus récents de l'équipe Visual C\#, consultez le [Centre de développement Visual C\#](http://go.microsoft.com/fwlink/?LinkId=47811).  
  
## Architecture de la plateforme du .NET Framework  
 Les programmes en C\# s'exécutent sur le [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)], composant intégral de Windows qui inclut un système d'exécution virtuel appelé Common Language Runtime \(CLR\) et un ensemble unifié de bibliothèques de classes.  Le CLR est l'implémentation commerciale de l'infrastructure du langage commun \(CLI, Common Language Infrastructure\) de Microsoft, norme internationale constituant la base de toute création d'environnements d'exécution et de développement et assurant le fonctionnement homogène des langages et des bibliothèques.  
  
 Le code source écrit en C\# est compilé dans un langage intermédiaire conforme à la spécification CLI.  Le code IL de ce langage intermédiaire, ainsi que les ressources telles que les bitmaps et les chaînes, sont stockés sur le disque dans un fichier exécutable appelé assembly, dont l'extension est généralement .exe ou .dll.  Un assembly contient un manifeste qui fournit des spécifications sur les types, la version, la culture et les conditions de sécurité de l'assembly.  
  
 À l'exécution du programme C\#, l'assembly est chargé dans le CLR, qui peut prendre différentes mesures sur la base des informations du manifeste.  Ensuite, si les conditions de sécurité sont respectées, le CLR effectue une compilation juste\-à\-temps pour convertir le code du langage intermédiaire en instructions machine natives.  Le CLR fournit également d'autres services en rapport avec les opérations automatiques de garbage collection et la gestion des exceptions et des ressources.  Le code exécuté par le CLR est quelquefois appelé « code managé », par contraste avec le « code non managé », compilé dans le langage machine natif ciblant un système spécifique.  Le diagramme suivant illustre les relations entre les temps de compilation et d'exécution des fichiers en code source C\#, des bibliothèques de classes .NET Framework, des assemblys et du CLR.  
  
 ![Du code source C&#35; à l'exécution machine](../../csharp/getting-started/media/netarchitecture.png "NETarchitecture")  
  
 L'interopérabilité des langages est une fonctionnalité clé du [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)].  Étant donné que le code IL \(Intermediate Language\) produit par le compilateur C\# respecte la spécification de type commun \(CTS\), il peut, lorsqu'il est généré à partir de C\#, interagir avec le code généré à partir des versions .NET de Visual Basic, Visual C\+\+, Visual J\# ou d'un des vingt autres langages respectant la norme CTS.  Un même assembly peut contenir plusieurs modules écrits dans différents langages .NET, et les types peuvent se référencer l'un l'autre exactement comme s'ils avaient été écrits dans le même langage.  
  
 Outre les services d'exécution, le [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)] inclut également une bibliothèque étendue de plus de 4 000 classes organisées en espaces de noms, qui fournissent une large gamme de fonctionnalités couvrant de nombreuses utilisations, de l'entrée\/sortie de fichiers aux contrôles Windows Forms, en passant par la manipulation de chaînes et l'analyse XML.  Une application C\# standard utilise largement la bibliothèque de classes [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)] pour assurer les tâches de maintenance courantes les plus fastidieuses.  
  
 Pour plus d'informations sur le .NET Framework, consultez [Overview of the Microsoft .NET Framework](http://msdn.microsoft.com/fr-fr/d05daf50-00fe-45c7-8383-06fe41697355).  
  
## Chapitres proposés  
 [C\# Language Fundamentals](http://go.microsoft.com/fwlink/?LinkId=195416) dans [Learning C\# 3.0: Master the fundamentals of C\# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)  
  
 [C\# and .NET Programming](http://go.microsoft.com/fwlink/?LinkId=195413) dans [Learning C\# 3.0: Master the fundamentals of C\# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)  
  
 [Présentation de C\#](http://go.microsoft.com/fwlink/?LinkId=221226) dans [Débuter avec Visual C\# 2010](http://go.microsoft.com/fwlink/?LinkId=221214)  
  
 [Visual Studio 2008 and C\# Express 2008](http://go.microsoft.com/fwlink/?LinkId=195414) dans [Learning C\# 3.0: Master the fundamentals of C\# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)  
  
## Voir aussi  
 [C\#](../../csharp/csharp.md)   
 [Mises en route de Visual Basic et Visual C\#](/visual-studio/ide/getting-started-with-visual-csharp-and-visual-basic)