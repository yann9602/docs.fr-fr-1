---
title: "Utilisation de la classe StringBuilder Class dans .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Remove (méthode)"
  - "chaînes (.NET Framework), capacités"
  - "StringBuilder (objet)"
  - "Replace (méthode)"
  - "AppendFormat (méthode)"
  - "Append (méthode)"
  - "Insert (méthode)"
  - "chaînes (.NET Framework), objet StringBuilder"
ms.assetid: 5c14867c-9a99-45bc-ae7f-2686700d377a
caps.latest.revision: 21
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# Utilisation de la classe StringBuilder Class dans .NET Framework
L’objet <xref:System.String> est immuable. Chaque fois que vous utilisez l’une des méthodes de la classe <xref:System.String?displayProperty=fullName>, vous créez un nouvel objet string en mémoire, ce qui nécessite une nouvelle allocation d’espace pour ce nouvel objet. Si vous devez effectuer des modifications répétées sur une chaîne, la surcharge associée à la création d’un objet <xref:System.String> peut être coûteuse. Vous pouvez utiliser la classe <xref:System.Text.StringBuilder?displayProperty=fullName> quand vous voulez modifier une chaîne sans créer d’objet. Par exemple, la classe <xref:System.Text.StringBuilder> permet d’améliorer les performances quand il s’agit de concaténer un grand nombre de chaînes dans une boucle.  
  
## Importation de l’espace de noms System.Type  
 La classe <xref:System.Text.StringBuilder> se trouve dans l’espace de noms <xref:System.Text>.  Pour éviter d’avoir à fournir un nom de type complet dans votre code, vous pouvez importer l’espace de noms <xref:System.Text> :  
  
 [!code-cpp[Conceptual.StringBuilder#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#11)]
 [!code-csharp[Conceptual.StringBuilder#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#11)]
 [!code-vb[Conceptual.StringBuilder#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#11)]  
  
## Instanciation d’un objet StringBuilder  
 Vous pouvez créer une nouvelle instance de la classe <xref:System.Text.StringBuilder> en initialisant votre variable avec l’une des méthodes de constructeur surchargées, comme l’illustre l’exemple suivant.  
  
 [!code-cpp[Conceptual.StringBuilder#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#1)]
 [!code-csharp[Conceptual.StringBuilder#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#1)]
 [!code-vb[Conceptual.StringBuilder#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#1)]  
  
## Définition de la capacité et de la longueur  
 Bien que <xref:System.Text.StringBuilder> soit un objet dynamique qui permet d’augmenter le nombre de caractères contenus dans la chaîne qu’il encapsule, vous pouvez spécifier une valeur pour le nombre maximal de caractères qu’elle peut contenir. Cette valeur est appelée « capacité » de l’objet et ne doit pas être confondue avec la longueur de la chaîne que l’instance actuelle de <xref:System.Text.StringBuilder> contient. Par exemple, vous pouvez créer une nouvelle instance de la classe <xref:System.Text.StringBuilder> avec la chaîne « Hello», dont la longueur est de 5, et préciser que l’objet a une capacité maximale de 25. Quand vous modifiez l’instance de <xref:System.Text.StringBuilder>, elle ne se réalloue pas une taille tant que la capacité maximale n’est pas atteinte. Quand cela se produit, le nouvel espace est alloué automatiquement et la capacité est doublée. Vous pouvez spécifier la capacité de la classe <xref:System.Text.StringBuilder> en utilisant l’un des constructeurs surchargés. L’exemple suivant spécifie que l’objet `MyStringBuilder` peut être étendu à 25 espaces, au maximum.  
  
 [!code-cpp[Conceptual.StringBuilder#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#2)]
 [!code-csharp[Conceptual.StringBuilder#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#2)]
 [!code-vb[Conceptual.StringBuilder#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#2)]  
  
 De plus, vous pouvez utiliser la propriété <xref:System.Text.StringBuilder.Capacity%2A> en lecture\/écriture pour définir la longueur maximale de votre objet. L’exemple suivant utilise la propriété **Capacity** propriété pour définir la longueur maximale de l’objet.  
  
 [!code-cpp[Conceptual.StringBuilder#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#3)]
 [!code-csharp[Conceptual.StringBuilder#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#3)]
 [!code-vb[Conceptual.StringBuilder#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#3)]  
  
 La méthode <xref:System.Text.StringBuilder.EnsureCapacity%2A> peut être utilisée pour vérifier la capacité de l’instance actuelle de **StringBuilder**. Si la capacité est supérieure à la valeur passée, aucune modification n’est apportée ; en revanche, si la capacité est inférieure à la valeur passée, la capacité actuelle est modifiée pour correspondre à la valeur passée.  
  
 Vous pouvez aussi afficher ou définir la propriété <xref:System.Text.StringBuilder.Length%2A>. Si vous attribuez à la propriété **Length** une valeur supérieure à celle de la propriété **Capacity**, la propriété **Capacity** prend automatiquement la valeur de la propriété **Length**. Si vous attribuez à la propriété **Length** une valeur inférieure à la longueur de la chaîne dans l’instance actuelle de **StringBuilder**, la chaîne se raccourcit.  
  
## Modification de la chaîne StringBuilder  
 Le tableau suivant répertorie les méthodes que vous pouvez utiliser pour modifier le contenu d’une instance de **StringBuilder**.  
  
|Nom de la méthode|Utilisation|  
|-----------------------|-----------------|  
|<xref:System.Text.StringBuilder.Append%2A?displayProperty=fullName>|Ajoute des informations à la fin de l’instance actuelle de **StringBuilder**.|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=fullName>|Remplace un spécificateur de format passé dans une chaîne avec du texte mis en forme.|  
|<xref:System.Text.StringBuilder.Insert%2A?displayProperty=fullName>|Insère une chaîne ou un objet dans l’index spécifié de l’instance actuelle de **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Remove%2A?displayProperty=fullName>|Supprime un nombre de caractères spécifié de l’instance actuelle de **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Replace%2A?displayProperty=fullName>|Remplace un caractère spécifié au niveau d’un index spécifié.|  
  
### Append  
 La méthode **Append** permet d’ajouter du texte ou une représentation sous forme de chaîne d’un objet à la fin d’une chaîne représentée par l’instance actuelle de **StringBuilder**. L’exemple suivant initialise une instance de **StringBuilder** à « Hello World » avant d’ajouter du texte à la fin de l’objet. L’espace est alloué automatiquement en fonction des besoins.  
  
 [!code-cpp[Conceptual.StringBuilder#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#4)]
 [!code-csharp[Conceptual.StringBuilder#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#4)]
 [!code-vb[Conceptual.StringBuilder#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#4)]  
  
### AppendFormat  
 La méthode <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=fullName> ajoute du texte à la fin de l’objet <xref:System.Text.StringBuilder>. Elle prend en charge la fonctionnalité de mise en forme composite \(pour plus d’informations, consultez [Mise en forme composite](../../../docs/standard/base-types/composite-formatting.md)\) en appelant l’implémentation <xref:System.IFormattable> des objets à mettre en forme. Par conséquent, elle accepte les chaînes de format standard pour les valeurs numériques, de date et d’heure et d’énumération, les chaînes de format personnalisé pour les valeurs numériques et de date et d’heure, ainsi que les chaînes de format définies pour des types personnalisés. \(Pour plus d’informations sur la mise en forme, consultez [Mise en forme des types](../../../docs/standard/base-types/formatting-types.md).\) Vous pouvez utiliser cette méthode pour personnaliser le format des variables et ajouter ces valeurs à une instance de <xref:System.Text.StringBuilder>. L’exemple suivant utilise la méthode <xref:System.Text.StringBuilder.AppendFormat%2A> pour placer une valeur entière mise en forme en tant que valeur monétaire à la fin d’un objet <xref:System.Text.StringBuilder>.  
  
 [!code-cpp[Conceptual.StringBuilder#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#5)]
 [!code-csharp[Conceptual.StringBuilder#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#5)]
 [!code-vb[Conceptual.StringBuilder#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#5)]  
  
### Insert  
 La méthode <xref:System.Text.StringBuilder.Insert%2A> ajoute une chaîne ou un objet à une position spécifiée dans l’objet <xref:System.Text.StringBuilder> actuel. L’exemple suivant utilise cette méthode pour insérer un mot à la sixième position d’un objet <xref:System.Text.StringBuilder>.  
  
 [!code-cpp[Conceptual.StringBuilder#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#6)]
 [!code-csharp[Conceptual.StringBuilder#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#6)]
 [!code-vb[Conceptual.StringBuilder#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#6)]  
  
### Remove  
 Vous pouvez utiliser la méthode **Remove** pour supprimer un nombre spécifié de caractères dans l’objet <xref:System.Text.StringBuilder> actuel, en partant d’un index de base zéro spécifié. L’exemple suivant utilise la méthode **Remove** pour raccourcir un objet <xref:System.Text.StringBuilder>.  
  
 [!code-cpp[Conceptual.StringBuilder#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#7)]
 [!code-csharp[Conceptual.StringBuilder#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#7)]
 [!code-vb[Conceptual.StringBuilder#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#7)]  
  
### Replace  
 La méthode **Replace** permet de remplacer des caractères dans l’objet <xref:System.Text.StringBuilder> par un autre caractère spécifié. L’exemple suivant utilise la méthode **Replace** pour rechercher toutes les instances du caractère point d’exclamation \(\!\) dans un objet <xref:System.Text.StringBuilder> et les remplace par le caractère point d’interrogation \(?\).  
  
 [!code-cpp[Conceptual.StringBuilder#8](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#8)]
 [!code-csharp[Conceptual.StringBuilder#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#8)]
 [!code-vb[Conceptual.StringBuilder#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#8)]  
  
## Conversion d’un objet StringBuilder en chaîne  
 Vous devez convertir l’objet <xref:System.Text.StringBuilder> en objet <xref:System.String> pour pouvoir passer la chaîne représentée par l’objet <xref:System.Text.StringBuilder> à une méthode qui a un paramètre <xref:System.String> ou pour l’afficher dans l’interface utilisateur. Pour effectuer cette conversion, vous devez appeler la méthode <xref:System.Text.StringBuilder.ToString%2A?displayProperty=fullName>. L’exemple suivant appelle un certain nombre de méthodes <xref:System.Text.StringBuilder>, puis appelle la méthode <xref:System.Text.StringBuilder.ToString?displayProperty=fullName> pour afficher la chaîne.  
  
 [!code-csharp[Conceptual.StringBuilder#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/tostringexample1.cs#10)]
 [!code-vb[Conceptual.StringBuilder#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/tostringexample1.vb#10)]  
  
## Voir aussi  
 <xref:System.Text.StringBuilder?displayProperty=fullName>   
 [Opérations de chaînes de base](../../../docs/standard/base-types/basic-string-operations.md)   
 [Mise en forme des types](../../../docs/standard/base-types/formatting-types.md)