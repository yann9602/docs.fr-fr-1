---
title: "Comment&#160;: it&#233;rer au sein d&#39;une arborescence de r&#233;pertoires (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "parcours de fichiers (C#)"
  - "itérer au sein de dossiers (C#)"
ms.assetid: c4be4a75-6b1b-46a7-9d38-bab353091ed7
caps.latest.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 10
---
# Comment&#160;: it&#233;rer au sein d&#39;une arborescence de r&#233;pertoires (Guide de programmation C#)
L'expression « itérer au sein d'une arborescence de répertoires » signifie accéder à chaque fichier des différents sous\-répertoires imbriqués d'un dossier racine spécifié, quel que soit le nombre de niveaux.  Vous ne devez pas nécessairement ouvrir chaque fichier.  Vous pouvez simplement récupérer le nom du fichier ou du sous\-répertoire en tant que `string` ou vous pouvez récupérer des informations supplémentaires sous la forme d'un objet <xref:System.IO.FileInfo?displayProperty=fullName> ou <xref:System.IO.DirectoryInfo?displayProperty=fullName>.  
  
> [!NOTE]
>  Dans Windows, les termes « répertoire » et « dossier » sont utilisés indifféremment.  Le texte de la documentation et de l'interface utilisateur utilise généralement le terme « dossier », mais la bibliothèque de classes [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] utilise le terme « répertoire ».  
  
 Dans le cas le plus simple, à savoir quand vous êtes sûr que vous disposez d'autorisations d'accès pour tous les répertoires situés sous une racine spécifiée, vous pouvez utiliser l'indicateur `System.IO.SearchOption.AllDirectories`.  Cet indicateur retourne tous les sous\-répertoires imbriqués qui correspondent au modèle spécifié.  L'exemple suivant montre comment utiliser cet indicateur.  
  
```c#  
root.GetDirectories("*.*", System.IO.SearchOption.AllDirectories);  
```  
  
 La faiblesse de cette approche réside dans le fait que si l'un des sous\-répertoires situés sous la racine spécifiée entraîne une <xref:System.IO.DirectoryNotFoundException> ou une <xref:System.UnauthorizedAccessException>, la méthode entière échoue et ne retourne pas de répertoires.  Il en va de même lorsque vous utilisez la méthode <xref:System.IO.DirectoryInfo.GetFiles%2A>.  Si vous devez gérer ces exceptions pour des sous\-dossiers spécifiques, vous devez parcourir l'arborescence de répertoires manuellement, comme l'illustrent les exemples suivants.  
  
 Lorsque vous parcourez une arborescence de répertoires manuellement, vous pouvez gérer les sous\-répertoires en premier \(*balayage pré\-ordre*\) ou les fichiers en premier \(*balayage post\-ordre*\).  Si vous effectuez un balayage pré\-ordre, vous parcourez l'arborescence entière sous le dossier actif avant d'itérer au sein des fichiers qui sont situés directement dans ce dossier.  Les exemples présentés ultérieurement dans ce document effectuent un balayage post\-ordre, mais vous pouvez les modifier facilement pour effectuer un balayage pré\-ordre.  
  
 Une autre option concerne l'utilisation de la récurrence ou d'un balayage de type pile.  Les exemples présentés ultérieurement dans ce document montrent les deux approches.  
  
 Si vous devez effectuer diverses opérations sur des fichiers et des dossiers, vous pouvez organiser ces exemples par modules en refactorisant l'opération en fonctions séparées que vous pouvez appeler en utilisant un délégué unique.  
  
> [!NOTE]
>  Les systèmes de fichiers NTFS peuvent contenir des *points d'analyse* sous la forme de *points de jonction*, de *liens physiques* et de *liens réels*.  Les méthodes .NET Framework telles que <xref:System.IO.DirectoryInfo.GetFiles%2A> et <xref:System.IO.DirectoryInfo.GetDirectories%2A> ne retournent pas de sous\-répertoires situés sous un point d'analyse.  Ce comportement empêche d'entrer dans une boucle infinie lorsque deux points d'analyse font référence l'un à l'autre.  En général, soyez extrêmement prudent lorsque vous utilisez des points d'analyse : vous risquez de modifier ou de supprimer des fichiers involontairement.  Si vous avez besoin d'un contrôle précis sur les points d'analyse, utilisez l'appel de code non managé ou le code natif pour appeler directement les méthodes de système de fichiers Win32 appropriées.  
  
## Exemple  
 L'exemple suivant montre comment parcourir une arborescence de répertoires à l'aide de la récurrence.  L'approche récursive est élégante, mais est susceptible de provoquer une exception de dépassement de capacité de la pile si l'arborescence de répertoires est importante et comporte un grand nombre de niveaux d'imbrication.  
  
 Les exceptions particulières gérées et les actions particulières effectuées sur chaque fichier ou dossier sont fournies uniquement à titre d'exemples.  Vous devez modifier ce code en fonction de vos besoins.  Pour plus d'informations, consultez les commentaires du code.  
  
 [!code-cs[csFilesandFolders#1](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-iterate-through-a-directory-tree_1.cs)]  
  
## Exemple  
 L'exemple suivant indique comment itérer au sein de fichiers et de dossiers dans une arborescence de répertoires sans utiliser la récurrence.  Cette technique utilise le type de collection générique <xref:System.Collections.Generic.Stack%601>, à savoir une pile de type dernier entré, premier sorti \(LIFO, Last\-In\-First\-Out\).  
  
 Les exceptions particulières gérées et les actions particulières effectuées sur chaque fichier ou dossier sont fournies uniquement à titre d'exemples.  Vous devez modifier ce code en fonction de vos besoins.  Pour plus d'informations, consultez les commentaires du code.  
  
 [!code-cs[csFilesandFolders#2](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-iterate-through-a-directory-tree_2.cs)]  
  
 Il est généralement trop long de tester chaque dossier afin de déterminer si votre application a l'autorisation de l'ouvrir.  Par conséquent, l'exemple de code englobe simplement cette partie de l'opération dans un bloc `try/catch`.  Vous pouvez modifier le bloc `catch` afin que, lorsque l'accès à un dossier vous est refusé, vous essayiez d'élever vos autorisations et d'y accéder de nouveau.  En règle générale, interceptez uniquement les exceptions que vous pouvez gérer sans laisser votre application dans un état inconnu.  
  
 Si vous devez stocker le contenu d'une arborescence de répertoires en mémoire ou sur le disque, la meilleure option est de stocker uniquement la propriété <xref:System.IO.FileSystemInfo.FullName%2A> \(de type `string`\) pour chaque fichier.  Vous pouvez utiliser ensuite cette chaîne pour créer au besoin un nouvel objet <xref:System.IO.FileInfo> ou <xref:System.IO.DirectoryInfo> ou pour ouvrir les fichiers qui requièrent un traitement supplémentaire.  
  
## Programmation fiable  
 Pour être fiables, les codes permettant d'itérer au sein des fichiers doivent prendre en considération les nombreuses complexités du système de fichiers.  Pour plus d'informations, consultez [NTFS Technical Reference](http://go.microsoft.com/fwlink/?LinkId=79488).  
  
## Voir aussi  
 <xref:System.IO>   
 [LINQ and File Directories](../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)   
 [Système de fichiers et Registre](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)