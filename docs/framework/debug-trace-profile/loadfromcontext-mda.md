---
title: "loadFromContext MDA | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MDAs (managed debugging assistants), LoadFrom context"
  - "managed debugging assistants (MDAs), LoadFrom context"
  - "LoadFrom context"
  - "LoadFromContext MDA"
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# loadFromContext MDA
L'Assistant Débogage managé \(MDA, Managed Debugging Assistant\) `loadFromContext` est activé si un assembly est chargé dans le contexte `LoadFrom`.  Cette situation peut se produire suite à l'appel de <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName> ou d'autres méthodes similaires.  
  
## Symptômes  
 L'utilisation de certaines méthodes de chargeur peut entraîner le chargement des assemblys dans le contexte `LoadFrom`.  L'utilisation de ce contexte peut entraîner un comportement imprévisible pour la sérialisation, le casting et la résolution de dépendance.  En général, il est recommandé de charger les assemblys dans le contexte `Load` pour éviter ces problèmes.  Il est difficile de déterminer le contexte dans lequel un assembly a été chargé sans ce MDA.  
  
## Cause  
 En général, un assembly a été chargé dans le contexte `LoadFrom` s'il a été chargé à partir d'un chemin d'accès qui se trouve en dehors du contexte `Load`, tel que le Global Assembly Cache ou la propriété <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=fullName>.  
  
## Résolution  
 Configurez les applications de sorte que les appels <xref:System.Reflection.Assembly.LoadFrom%2A> ne soient plus nécessaires.  Pour ce faire, vous pouvez utiliser les techniques suivantes :  
  
-   Installez les assemblys dans le Global Assembly Cache.  
  
-   Placez les assemblys dans le répertoire <xref:System.AppDomainSetup.ApplicationBase%2A> pour le <xref:System.AppDomain>.  Dans le cas du domaine par défaut, le répertoire <xref:System.AppDomainSetup.ApplicationBase%2A> est celui qui contient le fichier exécutable qui a démarré le processus.  La création d'un <xref:System.AppDomain> peut également être nécessaire si le déplacement de l'assembly n'est pas pratique.  
  
-   Ajoutez un chemin de détection au fichier de configuration \(.config\) de l'application ou aux domaines d'application secondaires si les assemblys dépendants se trouvent dans les répertoires enfants relatifs au fichier exécutable.  
  
 Dans chaque cas, le code peut être modifié pour utiliser la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>.  
  
## Effet sur le runtime  
 Le MDA n'a aucun effet sur le CLR.  Il signale le contexte qui a été utilisé suite à une demande de chargement.  
  
## Sortie  
 Le MDA signale que l'assembly a été chargé dans le contexte `LoadFrom`.  Il spécifie le nom simple de l'assembly et le chemin d'accès.  Il suggère également des atténuations pour éviter d'utiliser le contexte `LoadFrom`.  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## Exemple  
 L'exemple de code suivant illustre une situation qui peut activer ce MDA :  
  
```  
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // The following call caused the LoadFrom context to be used  
            // because the assembly is loaded using LoadFrom and the path is   
            // located outside of the Load context probing path.   
            Assembly.LoadFrom(@"C:\Text\Test.dll");  
        }  
    }  
}  
```  
  
## Voir aussi  
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)