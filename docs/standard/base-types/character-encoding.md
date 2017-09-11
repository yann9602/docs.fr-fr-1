---
title: "Encodage de caractères dans .NET"
description: "Encodage de caractères dans .NET"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: bce54e41-e9dc-493a-8988-1cbadc340fe8
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: a8f42fa6a37f8de6f13186ea2ac17b2b2ced1601
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="character-encoding-in-net"></a><span data-ttu-id="f9f27-104">Encodage de caractères dans .NET</span><span class="sxs-lookup"><span data-stu-id="f9f27-104">Character encoding in .NET</span></span>

<span data-ttu-id="f9f27-105">Les caractères sont des entités abstraites qui peuvent être représentées de nombreuses façons différentes.</span><span class="sxs-lookup"><span data-stu-id="f9f27-105">Characters are abstract entities that can be represented in many different ways.</span></span> <span data-ttu-id="f9f27-106">Un encodage de caractères est un système qui associe chaque caractère d'un jeu de caractères pris en charge à une valeur qui représente ce caractère.</span><span class="sxs-lookup"><span data-stu-id="f9f27-106">A character encoding is a system that pairs each character in a supported character set with some value that represents that character.</span></span> <span data-ttu-id="f9f27-107">Par exemple, le code Morse est un encodage de caractères qui associe chaque caractère de l'alphabet latin à une séquence de points et de tirets qui conviennent pour la transmission sur des lignes télégraphiques.</span><span class="sxs-lookup"><span data-stu-id="f9f27-107">For example, Morse code is a character encoding that pairs each character in the Roman alphabet with a pattern of dots and dashes that are suitable for transmission over telegraph lines.</span></span> <span data-ttu-id="f9f27-108">Un encodage de caractères pour les ordinateurs associe chaque caractère d'un jeu de caractères à une valeur numérique qui représente ce caractère.</span><span class="sxs-lookup"><span data-stu-id="f9f27-108">A character encoding for computers pairs each character in a supported character set with a numeric value that represents that character.</span></span> <span data-ttu-id="f9f27-109">Un encodage de caractères a deux composants distincts :</span><span class="sxs-lookup"><span data-stu-id="f9f27-109">A character encoding has two distinct components:</span></span>

* <span data-ttu-id="f9f27-110">Un encodeur, qui convertit une séquence de caractères en une séquence de valeurs numériques (octets).</span><span class="sxs-lookup"><span data-stu-id="f9f27-110">An encoder, which translates a sequence of characters into a sequence of numeric values (bytes).</span></span>

* <span data-ttu-id="f9f27-111">Un décodeur, qui convertit une séquence d'octets en une séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="f9f27-111">A decoder, which translates a sequence of bytes into a sequence of characters.</span></span>

<span data-ttu-id="f9f27-112">L'encodage de caractères décrit les règles selon lesquelles un encodeur et un décodeur fonctionnent.</span><span class="sxs-lookup"><span data-stu-id="f9f27-112">Character encoding describes the rules by which an encoder and a decoder operate.</span></span> <span data-ttu-id="f9f27-113">Par exemple, la classe [UTF8Encoding](xref:System.Text.UTF8Encoding) décrit les règles d’encodage et de décodage UTF-8, qui utilise de un à quatre octets pour représenter un caractère Unicode.</span><span class="sxs-lookup"><span data-stu-id="f9f27-113">For example, the [UTF8Encoding](xref:System.Text.UTF8Encoding) class describes the rules for encoding to, and decoding from, 8-bit Unicode Transformation Format (UTF-8), which uses one to four bytes to represent a single Unicode character.</span></span> <span data-ttu-id="f9f27-114">L’encodage et le décodage peuvent également inclure une validation.</span><span class="sxs-lookup"><span data-stu-id="f9f27-114">Encoding and decoding can also include validation.</span></span> <span data-ttu-id="f9f27-115">Par exemple, la classe [UnicodeEncoding](xref:System.Text.UnicodeEncoding) vérifie tous les substituts afin de vérifier qu’ils constituent des paires de substitution valide.</span><span class="sxs-lookup"><span data-stu-id="f9f27-115">For example, the [UnicodeEncoding](xref:System.Text.UnicodeEncoding) class checks all surrogates to make sure they constitute valid surrogate pairs.</span></span> <span data-ttu-id="f9f27-116">(Une paire de substitution se compose d'un caractère avec un point de code allant de U+D800 à U+DBFF, suivi d'un caractère avec un point de code allant de U+DC00 à U+DFFF.) Une stratégie de secours détermine comment un encodeur traite les caractères non valides ou comment un décodeur gère les octets non valides.</span><span class="sxs-lookup"><span data-stu-id="f9f27-116">(A surrogate pair consists of a character with a code point that ranges from U+D800 to U+DBFF followed by a character with a code point that ranges from U+DC00 to U+DFFF.) A fallback strategy determines how an encoder handles invalid characters or how a decoder handles invalid bytes.</span></span> 

> [!WARNING]
> <span data-ttu-id="f9f27-117">Les classes d’encodage .NET permettent de stocker et de convertir les données caractères.</span><span class="sxs-lookup"><span data-stu-id="f9f27-117">The .NET encoding classes provide a way to store and convert character data.</span></span> <span data-ttu-id="f9f27-118">Elles ne doivent pas utilisées pour stocker des données binaires sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="f9f27-118">They should not be used to store binary data in string form.</span></span> <span data-ttu-id="f9f27-119">En fonction de l'encodage utilisé, la conversion de données binaires en un format chaîne avec les classes d'encodage peut entraîner un comportement inattendu et produire des données incorrectes ou endommagées.</span><span class="sxs-lookup"><span data-stu-id="f9f27-119">Depending on the encoding used, converting binary data to string format with the encoding classes can introduce unexpected behavior and produce inaccurate or corrupted data.</span></span> <span data-ttu-id="f9f27-120">Pour convertir les données binaires en chaîne, utilisez la méthode [Convert.ToBase64String](xref:System.Convert.ToBase64String(System.Byte[])).</span><span class="sxs-lookup"><span data-stu-id="f9f27-120">To convert binary data to a string form, use the [Convert.ToBase64String](xref:System.Convert.ToBase64String(System.Byte[])) method.</span></span> 
 
<span data-ttu-id="f9f27-121">.NET utilise l’encodage UTF-16 (représenté par la classe [UnicodeEncoding](xref:System.Text.UnicodeEncoding)) pour représenter des caractères et des chaînes.</span><span class="sxs-lookup"><span data-stu-id="f9f27-121">.NET uses the UTF-16 encoding (represented by the [UnicodeEncoding](xref:System.Text.UnicodeEncoding) class) to represent characters and strings.</span></span> <span data-ttu-id="f9f27-122">Les applications qui ciblent le common language runtime utilisent des encodeurs pour mapper les représentations de caractères Unicode prises en charge par le common language runtime à d'autres schémas de codage.</span><span class="sxs-lookup"><span data-stu-id="f9f27-122">Applications that target the common language runtime use encoders to map Unicode character representations supported by the common language runtime to other encoding schemes.</span></span> <span data-ttu-id="f9f27-123">Elles utilisent des décodeurs pour mapper les caractères des encodages non-Unicode à Unicode.</span><span class="sxs-lookup"><span data-stu-id="f9f27-123">They use decoders to map characters from non-Unicode encodings to Unicode.</span></span>

<span data-ttu-id="f9f27-124">Cette rubrique contient les sections suivantes :</span><span class="sxs-lookup"><span data-stu-id="f9f27-124">This topic consists of the following sections:</span></span>

* [<span data-ttu-id="f9f27-125">Encodages dans .NET</span><span class="sxs-lookup"><span data-stu-id="f9f27-125">Encodings in .NET</span></span>](#encodings-in-net)

* [<span data-ttu-id="f9f27-126">Sélection d’une classe d’encodage</span><span class="sxs-lookup"><span data-stu-id="f9f27-126">Selecting an encoding class</span></span>](#selecting-an-encoding-class)

* [<span data-ttu-id="f9f27-127">Utilisation d’un objet d’encodage</span><span class="sxs-lookup"><span data-stu-id="f9f27-127">Using an encoding object</span></span>](#using-an-encoding-object)

* [<span data-ttu-id="f9f27-128">Choix d’une stratégie de secours</span><span class="sxs-lookup"><span data-stu-id="f9f27-128">Choosing a fallback strategy</span></span>](#choosing-a-fallback-strategy)

* [<span data-ttu-id="f9f27-129">Implémentation d’une stratégie de secours personnalisée</span><span class="sxs-lookup"><span data-stu-id="f9f27-129">Implementing a custom fallback strategy</span></span>](#implementing-a-custom-fallback-strategy)

## <a name="encodings-in-net"></a><span data-ttu-id="f9f27-130">Encodages dans .NET</span><span class="sxs-lookup"><span data-stu-id="f9f27-130">Encodings in .NET</span></span>

<span data-ttu-id="f9f27-131">Toutes les classes d’encodage de caractères dans .NET héritent de la classe [System.Text.Encoding](xref:System.Text.Encoding), qui est une classe abstraite définissant les fonctionnalités communes à tous les encodages de caractères.</span><span class="sxs-lookup"><span data-stu-id="f9f27-131">All character encoding classes in .NET inherit from the [System.Text.Encoding](xref:System.Text.Encoding) class, which is an abstract class that defines the functionality common to all character encodings.</span></span> <span data-ttu-id="f9f27-132">Pour accéder aux objets d’encodage individuels implémentés dans .NET, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="f9f27-132">To access the individual encoding objects implemented in .NET, do the following:</span></span>

* <span data-ttu-id="f9f27-133">Utilisez les propriétés statiques de la classe [Encoding](xref:System.Text.Encoding), qui retournent des objets représentant les encodages de caractères standard disponibles dans .NET (ASCII, UTF-7, UTF-8, UTF-16 et UTF-32).</span><span class="sxs-lookup"><span data-stu-id="f9f27-133">Use the static properties of the [Encoding](xref:System.Text.Encoding) class, which return objects that represent the standard character encodings available in .NET (ASCII, UTF-7, UTF-8, UTF-16, and UTF-32).</span></span> <span data-ttu-id="f9f27-134">Par exemple, la propriété [Encoding.Unicode](xref:System.Text.Encoding.Unicode) retourne un objet [UnicodeEncoding](xref:System.Text.UnicodeEncoding).</span><span class="sxs-lookup"><span data-stu-id="f9f27-134">For example, the [Encoding.Unicode](xref:System.Text.Encoding.Unicode) property returns a [UnicodeEncoding](xref:System.Text.UnicodeEncoding) object.</span></span> <span data-ttu-id="f9f27-135">Chaque objet utilise la stratégie de secours pour les remplacements pour traiter les chaînes qu'il ne peut pas encoder et les octets qu'il ne peut pas décoder.</span><span class="sxs-lookup"><span data-stu-id="f9f27-135">Each object uses replacement fallback to handle strings that it cannot encode and bytes that it cannot decode.</span></span> <span data-ttu-id="f9f27-136">(Pour plus d’informations, consultez la section [Stratégie de secours pour les remplacements](#replacement-fallback).)</span><span class="sxs-lookup"><span data-stu-id="f9f27-136">(For more information, see the [Replacement fallback](#replacement-fallback) section.)</span></span>

* <span data-ttu-id="f9f27-137">Appelez le constructeur de classe de l'encodage.</span><span class="sxs-lookup"><span data-stu-id="f9f27-137">Call the encoding's class constructor.</span></span> <span data-ttu-id="f9f27-138">Les objets pour les encodages ASCII, UTF-7, UTF-8, UTF-16 et UTF-32 peuvent être instanciés de cette façon.</span><span class="sxs-lookup"><span data-stu-id="f9f27-138">Objects for the ASCII, UTF-7, UTF-8, UTF-16, and UTF-32 encodings can be instantiated in this way.</span></span> <span data-ttu-id="f9f27-139">Par défaut, chaque objet utilise la stratégie de secours pour les remplacements pour traiter les chaînes qu'il ne peut pas encoder et les octets qu'il ne peut pas décoder, mais vous pouvez spécifier qu'au lieu de cela, une exception doit être levée.</span><span class="sxs-lookup"><span data-stu-id="f9f27-139">By default, each object uses replacement fallback to handle strings that it cannot encode and bytes that it cannot decode, but you can specify that an exception should be thrown instead.</span></span> <span data-ttu-id="f9f27-140">(Pour plus d’informations, consultez les sections [Stratégie de secours pour les remplacements](#replacement-fallback) et [Stratégie de secours pour les exceptions](#exception-fallback).)</span><span class="sxs-lookup"><span data-stu-id="f9f27-140">(For more information, see the [Replacement fallback](#replacement-fallback) and [Exception fallback](#exception-fallback) sections.)</span></span>

* <span data-ttu-id="f9f27-141">Appelez le constructeur [Encoding.Encoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) et passez-lui un entier qui représente l’encodage.</span><span class="sxs-lookup"><span data-stu-id="f9f27-141">Call the [Encoding.Encoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) constructor and pass it an integer that represents the encoding.</span></span> <span data-ttu-id="f9f27-142">Les objets d'encodage standard utilisent la stratégie de secours pour les remplacements. Les objets d'encodage de page de codes et de jeu de caractères codés sur deux octets (DBCS) utilisent la stratégie de secours la mieux adaptée pour traiter les chaînes qu'ils ne peuvent pas encoder et les octets qu'ils ne peuvent pas décoder.</span><span class="sxs-lookup"><span data-stu-id="f9f27-142">Standard encoding objects use replacement fallback, and code page and double-byte character set (DBCS) encoding objects use best-fit fallback to handle strings that they cannot encode and bytes that they cannot decode.</span></span> <span data-ttu-id="f9f27-143">(Pour plus d’informations, consultez la section [Stratégie de secours la mieux adaptée](#best-fit-fallback).)</span><span class="sxs-lookup"><span data-stu-id="f9f27-143">(For more information, see the [Best-Fit fallback](#best-fit-fallback) section.)</span></span>

* <span data-ttu-id="f9f27-144">Appelez la méthode [Encoding.GetEncoding](xref:System.Text.Encoding.GetEncoding(System.Int32)), qui retourne les encodages standard, de page de codes ou DBCS disponibles dans .NET.</span><span class="sxs-lookup"><span data-stu-id="f9f27-144">Call the [Encoding.GetEncoding](xref:System.Text.Encoding.GetEncoding(System.Int32)) method, which returns any standard, code page, or DBCS encoding available in .NET.</span></span> <span data-ttu-id="f9f27-145">Les surcharges vous permettent de spécifier un objet de secours pour l'encodeur et pour le décodeur.</span><span class="sxs-lookup"><span data-stu-id="f9f27-145">Overloads let you specify a fallback object for both the encoder and the decoder.</span></span>

> [!NOTE]
> <span data-ttu-id="f9f27-146">La norme Unicode affecte un point de code (un nombre) et un nom à chaque caractère de chaque jeu de caractères pris en charge.</span><span class="sxs-lookup"><span data-stu-id="f9f27-146">The Unicode Standard assigns a code point (a number) and a name to each character in every supported script.</span></span> <span data-ttu-id="f9f27-147">Par exemple, le caractère "A" est représenté par le point de code U+0041 et par le nom "LETTRE MAJUSCULE LATINE A".</span><span class="sxs-lookup"><span data-stu-id="f9f27-147">For example, the character "A" is represented by the code point U+0041 and the name "LATIN CAPITAL LETTER A".</span></span> <span data-ttu-id="f9f27-148">Les encodages UTF (Unicode Transformation Format) définissent des moyens d'encoder ce point de code en une séquence d'un ou plusieurs octets.</span><span class="sxs-lookup"><span data-stu-id="f9f27-148">The Unicode Transformation Format (UTF) encodings define ways to encode that code point into a sequence of one or more bytes.</span></span> <span data-ttu-id="f9f27-149">Un schéma d'encodage Unicode simplifie le développement d'applications mondialisées, car il permet la représentation avec un encodage unique des caractères provenant de n'importe quel jeu de caractères.</span><span class="sxs-lookup"><span data-stu-id="f9f27-149">A Unicode encoding scheme simplifies world-ready application development because it allows characters from any character set to be represented in a single encoding.</span></span> <span data-ttu-id="f9f27-150">Les développeurs d'applications ne doivent plus faire le suivi du schéma d'encodage qui a été utilisé pour produire des caractères pour une langue ou un système d'écriture spécifique, et les données peuvent être partagées entre des systèmes à une échelle internationale sans risque d'endommagement.</span><span class="sxs-lookup"><span data-stu-id="f9f27-150">Application developers no longer have to keep track of the encoding scheme that was used to produce characters for a specific language or writing system, and data can be shared among systems internationally without being corrupted.</span></span>
>
>  <span data-ttu-id="f9f27-151">.NET prend en charge trois encodages définis par la norme Unicode : UTF-8, UTF-16 et UTF-32.</span><span class="sxs-lookup"><span data-stu-id="f9f27-151">.NET supports three encodings defined by the Unicode standard: UTF-8, UTF-16, and UTF-32.</span></span> <span data-ttu-id="f9f27-152">Pour plus d’informations, consultez la norme Unicode dans la page d’accueil [Unicode](http://www.unicode.org/).</span><span class="sxs-lookup"><span data-stu-id="f9f27-152">For more information, see The Unicode Standard at the [Unicode](http://www.unicode.org/) home page.</span></span>
 
<span data-ttu-id="f9f27-153">.NET prend en charge les systèmes d’encodage de caractères répertoriés dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="f9f27-153">.NET supports the character encoding systems listed in the following table.</span></span>

<span data-ttu-id="f9f27-154">Encodage</span><span class="sxs-lookup"><span data-stu-id="f9f27-154">Encoding</span></span> | <span data-ttu-id="f9f27-155">Classe</span><span class="sxs-lookup"><span data-stu-id="f9f27-155">Class</span></span> | <span data-ttu-id="f9f27-156">Description</span><span class="sxs-lookup"><span data-stu-id="f9f27-156">Description</span></span> | <span data-ttu-id="f9f27-157">Avantages et inconvénients</span><span class="sxs-lookup"><span data-stu-id="f9f27-157">Advantages/disadvantages</span></span>
-------- | ----- | ----------- | ------------------------ 
<span data-ttu-id="f9f27-158">ASCII</span><span class="sxs-lookup"><span data-stu-id="f9f27-158">ASCII</span></span> | [<span data-ttu-id="f9f27-159">ASCIIEncoding</span><span class="sxs-lookup"><span data-stu-id="f9f27-159">ASCIIEncoding</span></span>](xref:System.Text.ASCIIEncoding) | <span data-ttu-id="f9f27-160">Encode une plage de caractères limitée en utilisant les sept bits de poids le plus faible d'un octet.</span><span class="sxs-lookup"><span data-stu-id="f9f27-160">Encodes a limited range of characters by using the lower seven bits of a byte.</span></span> | <span data-ttu-id="f9f27-161">Étant donné que cet encodage prend en charge seulement des valeurs de caractère de U+0000 à U+007F, dans la plupart des cas, il ne convient pas aux applications internationalisées.</span><span class="sxs-lookup"><span data-stu-id="f9f27-161">Because this encoding only supports character values from U+0000 through U+007F, in most cases it is inadequate for internationalized applications.</span></span>
<span data-ttu-id="f9f27-162">UTF-7</span><span class="sxs-lookup"><span data-stu-id="f9f27-162">UTF-7</span></span> | [<span data-ttu-id="f9f27-163">UTF7Encoding</span><span class="sxs-lookup"><span data-stu-id="f9f27-163">UTF7Encoding</span></span>](xref:System.Text.UTF7Encoding) | <span data-ttu-id="f9f27-164">Représente les caractères sous forme de séquences de caractères ASCII sur 7 bits.</span><span class="sxs-lookup"><span data-stu-id="f9f27-164">Represents characters as sequences of 7-bit ASCII characters.</span></span> <span data-ttu-id="f9f27-165">Les caractères Unicode non-ASCII sont représentés par une séquence d'échappement de caractères ASCII.</span><span class="sxs-lookup"><span data-stu-id="f9f27-165">Non-ASCII Unicode characters are represented by an escape sequence of ASCII characters.</span></span> | <span data-ttu-id="f9f27-166">UTF-7 prend en charge les protocoles de messagerie et les protocoles de groupe de discussion.</span><span class="sxs-lookup"><span data-stu-id="f9f27-166">UTF-7 supports protocols such as e-mail and newsgroup protocols.</span></span> <span data-ttu-id="f9f27-167">UTF-7 n'est cependant pas particulièrement sécurisé ou robuste.</span><span class="sxs-lookup"><span data-stu-id="f9f27-167">However, UTF-7 is not particularly secure or robust.</span></span> <span data-ttu-id="f9f27-168">Dans certains cas, la modification d'un seul bit peut changer radicalement l'interprétation de toute une chaîne UTF-7.</span><span class="sxs-lookup"><span data-stu-id="f9f27-168">In some cases, changing one bit can radically alter the interpretation of an entire UTF-7 string.</span></span> <span data-ttu-id="f9f27-169">Dans d'autres cas, des chaînes UTF-7 différentes peuvent correspondre à l'encodage d'un même texte.</span><span class="sxs-lookup"><span data-stu-id="f9f27-169">In other cases, different UTF-7 strings can encode the same text.</span></span> <span data-ttu-id="f9f27-170">Pour les séquences incluant des caractères non-ASCII, UTF-7 nécessite davantage d'espace qu'UTF-8, et l'encodage/décodage est plus lent.</span><span class="sxs-lookup"><span data-stu-id="f9f27-170">For sequences that include non-ASCII characters, UTF-7 requires more space than UTF-8, and encoding/decoding is slower.</span></span> <span data-ttu-id="f9f27-171">Par conséquent, il est préférable d'utiliser UTF-8 au lieu d'UTF-7 si c'est possible.</span><span class="sxs-lookup"><span data-stu-id="f9f27-171">Consequently, you should use UTF-8 instead of UTF-7 if possible.</span></span>
<span data-ttu-id="f9f27-172">UTF-8</span><span class="sxs-lookup"><span data-stu-id="f9f27-172">UTF-8</span></span> | [<span data-ttu-id="f9f27-173">UTF8Encoding</span><span class="sxs-lookup"><span data-stu-id="f9f27-173">UTF8Encoding</span></span>](xref:System.Text.UTF8Encoding) | <span data-ttu-id="f9f27-174">Représente chaque point de code Unicode sous la forme d'une séquence de un à quatre octets.</span><span class="sxs-lookup"><span data-stu-id="f9f27-174">Represents each Unicode code point as a sequence of one to four bytes.</span></span> | <span data-ttu-id="f9f27-175">UTF-8 prend en charge des tailles de données de 8 bits et fonctionne bien avec de nombreux systèmes d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="f9f27-175">UTF-8 supports 8-bit data sizes and works well with many existing operating systems.</span></span> <span data-ttu-id="f9f27-176">Pour la plage de caractères ASCII, UTF-8 est identique à l'encodage ASCII et permet un ensemble de caractères plus large.</span><span class="sxs-lookup"><span data-stu-id="f9f27-176">For the ASCII range of characters, UTF-8 is identical to ASCII encoding and allows a broader set of characters.</span></span> <span data-ttu-id="f9f27-177">Cependant, pour les jeux de caractères Chinois-Japonais-Coréen (CJC), UTF-8 peut nécessiter trois octets pour chaque caractère et aboutir potentiellement à des tailles de données supérieures à celles d'UTF-16.</span><span class="sxs-lookup"><span data-stu-id="f9f27-177">However, for Chinese-Japanese-Korean (CJK) scripts, UTF-8 can require three bytes for each character, and can potentially cause larger data sizes than UTF-16.</span></span> <span data-ttu-id="f9f27-178">Notez que parfois, la quantité de données ASCII, comme des balises HTML, justifie l'augmentation de la taille pour les jeux de caractères CJC.</span><span class="sxs-lookup"><span data-stu-id="f9f27-178">Note that sometimes the amount of ASCII data, such as HTML tags, justifies the increased size for the CJK range.</span></span>
<span data-ttu-id="f9f27-179">UTF-16</span><span class="sxs-lookup"><span data-stu-id="f9f27-179">UTF-16</span></span> | [<span data-ttu-id="f9f27-180">UnicodeEncoding</span><span class="sxs-lookup"><span data-stu-id="f9f27-180">UnicodeEncoding</span></span>](xref:System.Text.UnicodeEncoding) | <span data-ttu-id="f9f27-181">Représente chaque point de code Unicode sous la forme d'une séquence de un ou deux entiers sur 16 bits.</span><span class="sxs-lookup"><span data-stu-id="f9f27-181">Represents each Unicode code point as a sequence of one or two 16-bit integers.</span></span> <span data-ttu-id="f9f27-182">La plupart des caractères Unicode courants ne nécessitent qu'un seul point de code UTF-16, tandis que les caractères Unicode additionnels (U+10000 et supérieurs) nécessitent deux points de code de substitution UTF-16.</span><span class="sxs-lookup"><span data-stu-id="f9f27-182">Most common Unicode characters require only one UTF-16 code point, although Unicode supplementary characters (U+10000 and greater) require two UTF-16 surrogate code points.</span></span> <span data-ttu-id="f9f27-183">Les ordres des octets Little Endian et Big Endian sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="f9f27-183">Both little-endian and big-endian byte orders are supported.</span></span> | <span data-ttu-id="f9f27-184">L’encodage UTF-16 est utilisé par le Common Language Runtime pour représenter les valeurs Char et String, et il est utilisé par le système d’exploitation Windows pour représenter les valeurs WCHAR.</span><span class="sxs-lookup"><span data-stu-id="f9f27-184">UTF-16 encoding is used by the common language runtime to represent Char and String values, and it is used by the Windows operating system to represent WCHAR values.</span></span>
<span data-ttu-id="f9f27-185">UTF-32</span><span class="sxs-lookup"><span data-stu-id="f9f27-185">UTF-32</span></span> | [<span data-ttu-id="f9f27-186">UTF32Encoding</span><span class="sxs-lookup"><span data-stu-id="f9f27-186">UTF32Encoding</span></span>](xref:System.Text.UTF32Encoding) | <span data-ttu-id="f9f27-187">Représente chaque point de code Unicode sous la forme d'un entier 32 bits.</span><span class="sxs-lookup"><span data-stu-id="f9f27-187">Represents each Unicode code point as a 32-bit integer.</span></span> <span data-ttu-id="f9f27-188">Les ordres des octets Little Endian et Big Endian sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="f9f27-188">Both little-endian and big-endian byte orders are supported.</span></span> | <span data-ttu-id="f9f27-189">L'encodage UTF-32 est utilisé quand les applications ne doivent pas avoir le comportement du point de code de substitution de l'encodage UTF-16 sur les systèmes d'exploitation pour lesquels l'espace encodé est trop important.</span><span class="sxs-lookup"><span data-stu-id="f9f27-189">UTF-32 encoding is used when applications want to avoid the surrogate code point behavior of UTF-16 encoding on operating systems for which encoded space is too important.</span></span> <span data-ttu-id="f9f27-190">Les glyphes uniques restitués à l'affichage peuvent néanmoins encore être encodés avec plusieurs caractères UTF-32.</span><span class="sxs-lookup"><span data-stu-id="f9f27-190">Single glyphs rendered on a display can still be encoded with more than one UTF-32 character.</span></span>

<span data-ttu-id="f9f27-191">Ces encodages vous permettent de travailler avec des caractères Unicode ainsi qu'avec les encodages les plus couramment utilisés dans les applications héritées.</span><span class="sxs-lookup"><span data-stu-id="f9f27-191">These encodings enable you to work with Unicode characters as well as with encodings that are most commonly used in legacy applications.</span></span> <span data-ttu-id="f9f27-192">En outre, vous pouvez créer un encodage personnalisé en définissant une classe qui dérive de [Encoding](xref:System.Text.Encoding) et en remplaçant ses membres.</span><span class="sxs-lookup"><span data-stu-id="f9f27-192">In addition, you can create a custom encoding by defining a class that derives from [Encoding](xref:System.Text.Encoding) and overriding its members.</span></span>

> [!NOTE]
> <span data-ttu-id="f9f27-193">Par défaut, .NET Core ne met à disposition aucune page de codes autre que la page de codes 28591 et les encodages Unicode, comme UTF-8 et UTF-16.</span><span class="sxs-lookup"><span data-stu-id="f9f27-193">By default, .NET Core does not make available any code page encodings other than code page 28591 and the Unicode encodings, such as UTF-8 and UTF-16.</span></span> <span data-ttu-id="f9f27-194">Vous pouvez cependant ajouter à votre application les encodages des pages de code qui se trouvent dans les applications Windows standard ciblant le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f9f27-194">However, you can add the code page encodings found in standard Windows apps that target the .NET Framework to your app.</span></span> <span data-ttu-id="f9f27-195">Pour plus d’informations, consultez la rubrique [EncodingProvider](xref:System.Text.EncodingProvider).</span><span class="sxs-lookup"><span data-stu-id="f9f27-195">For complete information, see the [EncodingProvider](xref:System.Text.EncodingProvider) topic.</span></span> 

## <a name="selecting-an-encoding-class"></a><span data-ttu-id="f9f27-196">Sélection d’une classe d’encodage</span><span class="sxs-lookup"><span data-stu-id="f9f27-196">Selecting an Encoding class</span></span>

<span data-ttu-id="f9f27-197">Si vous avez la possibilité de choisir l’encodage utilisé par votre application, utilisez un encodage Unicode, de préférence [UTF8Encoding](xref:System.Text.UTF8Encoding) ou [UnicodeEncoding](xref:System.Text.UnicodeEncoding).</span><span class="sxs-lookup"><span data-stu-id="f9f27-197">If you have the opportunity to choose the encoding to be used by your application, you should use a Unicode encoding, preferably either [UTF8Encoding](xref:System.Text.UTF8Encoding) or [UnicodeEncoding](xref:System.Text.UnicodeEncoding).</span></span> <span data-ttu-id="f9f27-198">(.NET prend également en charge un troisième encodage Unicode, [UTF32Encoding](xref:System.Text.UTF32Encoding).)</span><span class="sxs-lookup"><span data-stu-id="f9f27-198">(.NET also supports a third Unicode encoding, [UTF32Encoding](xref:System.Text.UTF32Encoding).)</span></span> 

<span data-ttu-id="f9f27-199">Si vous envisagez d’utiliser un encodage ASCII ([ASCIIEncoding](xref:System.Text.ASCIIEncoding)), choisissez [UTF8Encoding](xref:System.Text.UTF8Encoding) à la place.</span><span class="sxs-lookup"><span data-stu-id="f9f27-199">If you are planning to use an ASCII encoding ([ASCIIEncoding](xref:System.Text.ASCIIEncoding)), choose [UTF8Encoding](xref:System.Text.UTF8Encoding) instead.</span></span> <span data-ttu-id="f9f27-200">Les deux encodages sont identiques pour le jeu de caractères ASCII, mais [UTF8Encoding](xref:System.Text.UTF8Encoding) présente les avantages suivants :</span><span class="sxs-lookup"><span data-stu-id="f9f27-200">The two encodings are identical for the ASCII character set, but [UTF8Encoding](xref:System.Text.UTF8Encoding) has the following advantages:</span></span> 

* <span data-ttu-id="f9f27-201">Il peut représenter tous les caractères Unicode, alors qu’[ASCIIEncoding](xref:System.Text.ASCIIEncoding) prend en charge seulement les valeurs des caractères Unicode comprises entre U+0000 et U+007F.</span><span class="sxs-lookup"><span data-stu-id="f9f27-201">It can represent every Unicode character, whereas [ASCIIEncoding](xref:System.Text.ASCIIEncoding) supports only the Unicode character values between U+0000 and U+007F.</span></span>

* <span data-ttu-id="f9f27-202">Il offre une fonction de détection d'erreur et une meilleure sécurité.</span><span class="sxs-lookup"><span data-stu-id="f9f27-202">It provides error detection and better security.</span></span>

* <span data-ttu-id="f9f27-203">Il a été optimisé pour être aussi rapide que possible et il doit normalement être plus rapide n'importe quel autre encodage.</span><span class="sxs-lookup"><span data-stu-id="f9f27-203">It has been tuned to be as fast as possible and should be faster than any other encoding.</span></span> <span data-ttu-id="f9f27-204">Même pour du contenu qui est entièrement en ASCII, les opérations effectuées avec [UTF8Encoding](xref:System.Text.UTF8Encoding) sont plus rapides que les celles effectuées avec [ASCIIEncoding](xref:System.Text.ASCIIEncoding).</span><span class="sxs-lookup"><span data-stu-id="f9f27-204">Even for content that is entirely ASCII, operations performed with [UTF8Encoding](xref:System.Text.UTF8Encoding) are faster than operations performed with [ASCIIEncoding](xref:System.Text.ASCIIEncoding).</span></span>

<span data-ttu-id="f9f27-205">Il est préférable d’utiliser [ASCIIEncoding](xref:System.Text.ASCIIEncoding) seulement pour les applications héritées.</span><span class="sxs-lookup"><span data-stu-id="f9f27-205">You should consider using [ASCIIEncoding](xref:System.Text.ASCIIEncoding) only for legacy applications.</span></span> <span data-ttu-id="f9f27-206">Cependant, même pour les applications héritées, [UTF8Encoding](xref:System.Text.UTF8Encoding) peut être un meilleur choix pour les raisons suivantes (en supposant que les paramètres par défaut sont utilisés) :</span><span class="sxs-lookup"><span data-stu-id="f9f27-206">However, even for legacy applications, [UTF8Encoding](xref:System.Text.UTF8Encoding) might be a better choice for the following reasons (assuming default settings):</span></span>

* <span data-ttu-id="f9f27-207">Si votre application a du contenu qui n’est pas strictement ASCII et qu’elle l’encode avec [ASCIIEncoding](xref:System.Text.ASCIIEncoding), chaque caractère non-ASCII est encodé sous la forme d’un point d’interrogation (?).</span><span class="sxs-lookup"><span data-stu-id="f9f27-207">If your application has content that is not strictly ASCII and encodes it with [ASCIIEncoding](xref:System.Text.ASCIIEncoding), each non-ASCII character encodes as a question mark (?).</span></span> <span data-ttu-id="f9f27-208">Si l'application décode ensuite ces données, les informations sont perdues.</span><span class="sxs-lookup"><span data-stu-id="f9f27-208">If the application then decodes this data, the information is lost.</span></span>


* <span data-ttu-id="f9f27-209">Si votre application a du contenu qui n’est pas strictement ASCII et qu’elle l’encode avec [UTF8Encoding](xref:System.Text.UTF8Encoding), le résultat paraît inintelligible s’il est interprété comme étant en ASCII.</span><span class="sxs-lookup"><span data-stu-id="f9f27-209">If your application has content that is not strictly ASCII and encodes it with [UTF8Encoding](xref:System.Text.UTF8Encoding), the result seems unintelligible if interpreted as ASCII.</span></span> <span data-ttu-id="f9f27-210">Cependant, si l'application utilise ensuite un décodeur UTF-8 pour décoder ces données, les données apparaissent à nouveau correctes.</span><span class="sxs-lookup"><span data-stu-id="f9f27-210">However, if the application then uses a UTF-8 decoder to decode this data, the data performs a round trip successfully.</span></span>

<span data-ttu-id="f9f27-211">Dans une application web, les caractères envoyés au client en réponse à une demande web doivent refléter l'encodage utilisé sur le client.</span><span class="sxs-lookup"><span data-stu-id="f9f27-211">In a web application, characters sent to the client in response to a web request should reflect the encoding used on the client.</span></span> <span data-ttu-id="f9f27-212">Dans la plupart des cas, vous devez affecter à la propriété [HttpResponse.ContentEncoding](xref:System.Net.HttpResponseHeader.ContentEncoding) la valeur retournée par la propriété [HttpRequestHeader.ContentEncoding](xref:System.Net.HttpRequestHeader.ContentEncoding) pour afficher le texte dans l’encodage attendu par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f9f27-212">In most cases, you should set the [HttpResponse.ContentEncoding](xref:System.Net.HttpResponseHeader.ContentEncoding) property to the value returned by the [HttpRequestHeader.ContentEncoding](xref:System.Net.HttpRequestHeader.ContentEncoding) property to display text in the encoding that the user expects.</span></span>

## <a name="using-an-encoding-object"></a><span data-ttu-id="f9f27-213">Utilisation d’un objet d’encodage</span><span class="sxs-lookup"><span data-stu-id="f9f27-213">Using an encoding object</span></span>

<span data-ttu-id="f9f27-214">Un encodeur convertit une chaîne de caractères (le plus souvent, des caractères Unicode) en son équivalent numérique (en octets).</span><span class="sxs-lookup"><span data-stu-id="f9f27-214">An encoder converts a string of characters (most commonly, Unicode characters) to its numeric (byte) equivalent.</span></span> <span data-ttu-id="f9f27-215">Par exemple, vous pouvez utiliser un encodeur ASCII pour convertir des caractères Unicode en ASCII, pour pouvoir les afficher sur la console.</span><span class="sxs-lookup"><span data-stu-id="f9f27-215">For example, you might use an ASCII encoder to convert Unicode characters to ASCII so that they can be displayed at the console.</span></span> <span data-ttu-id="f9f27-216">Pour effectuer la conversion, vous appelez la méthode [Encoding.GetBytes](xref:System.Text.Encoding.GetBytes(System.Char[])).</span><span class="sxs-lookup"><span data-stu-id="f9f27-216">To perform the conversion, you call the [Encoding.GetBytes](xref:System.Text.Encoding.GetBytes(System.Char[])) method.</span></span> <span data-ttu-id="f9f27-217">Pour déterminer le nombre d’octets nécessaires pour stocker les caractères encodés avant de procéder à l’encodage, vous pouvez appeler la méthode [GetByteCount](xref:System.Text.Encoding.GetByteCount(System.Char[])).</span><span class="sxs-lookup"><span data-stu-id="f9f27-217">If you want to determine how many bytes are needed to store the encoded characters before performing the encoding, you can call the [GetByteCount](xref:System.Text.Encoding.GetByteCount(System.Char[])) method.</span></span>

<span data-ttu-id="f9f27-218">L'exemple suivant utilise un tableau d'octets seuls pour encoder des chaînes dans deux opérations distinctes.</span><span class="sxs-lookup"><span data-stu-id="f9f27-218">The following example uses a single byte array to encode strings in two separate operations.</span></span> <span data-ttu-id="f9f27-219">Il gère un index qui indique la position de départ dans le tableau d'octets pour l'ensemble suivant d'octets encodés en ASCII.</span><span class="sxs-lookup"><span data-stu-id="f9f27-219">It maintains an index that indicates the starting position in the byte array for the next set of ASCII-encoded bytes.</span></span> <span data-ttu-id="f9f27-220">Il appelle la méthode [ASCIIEncoding.GetByteCount(String)](xref:System.Text.ASCIIEncoding.GetByteCount(System.String)) pour vérifier que le tableau d’octets est assez grand pour contenir la chaîne encodée.</span><span class="sxs-lookup"><span data-stu-id="f9f27-220">It calls the [ASCIIEncoding.GetByteCount(String)](xref:System.Text.ASCIIEncoding.GetByteCount(System.String)) method to ensure that the byte array is large enough to accommodate the encoded string.</span></span> <span data-ttu-id="f9f27-221">Il appelle ensuite la méthode [ASCIIEncoding.GetBytes(String, Int32, Int32, Byte[], Int32)](xref:System.Text.ASCIIEncoding.GetBytes(System.Char[],System.Int32,System.Int32,System.Byte[],System.Int32)) pour encoder les caractères dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="f9f27-221">It then calls the [ASCIIEncoding.GetBytes(String, Int32, Int32, Byte[], Int32)](xref:System.Text.ASCIIEncoding.GetBytes(System.Char[],System.Int32,System.Int32,System.Byte[],System.Int32)) method to encode the characters in the string.</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      string[] strings= { "This is the first sentence. ", 
                          "This is the second sentence. " };
      Encoding asciiEncoding = Encoding.ASCII;

      // Create array of adequate size.
      byte[] bytes = new byte[49];
      // Create index for current position of array.
      int index = 0;

      Console.WriteLine("Strings to encode:");
      foreach (var stringValue in strings) {
         Console.WriteLine("   {0}", stringValue);

         int count = asciiEncoding.GetByteCount(stringValue);
         if (count + index >=  bytes.Length)
            Array.Resize(ref bytes, bytes.Length + 50);

         int written = asciiEncoding.GetBytes(stringValue, 0, 
                                              stringValue.Length, 
                                              bytes, index);    

         index = index + written; 
      } 
      Console.WriteLine("\nEncoded bytes:");
      Console.WriteLine("{0}", ShowByteValues(bytes, index));
      Console.WriteLine();

      // Decode Unicode byte array to a string.
      string newString = asciiEncoding.GetString(bytes, 0, index);
      Console.WriteLine("Decoded: {0}", newString);
   }

   private static string ShowByteValues(byte[] bytes, int last ) 
   {
      string returnString = "   ";
      for (int ctr = 0; ctr <= last - 1; ctr++) {
         if (ctr % 20 == 0)
            returnString += "\n   ";
         returnString += String.Format("{0:X2} ", bytes[ctr]);
      }
      return returnString;
   }
}
// The example displays the following output:
//       Strings to encode:
//          This is the first sentence.
//          This is the second sentence.
//       
//       Encoded bytes:
//       
//          54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
//          6E 74 65 6E 63 65 2E 20 54 68 69 73 20 69 73 20 74 68 65 20
//          73 65 63 6F 6E 64 20 73 65 6E 74 65 6E 63 65 2E 20
//       
//       Decoded: This is the first sentence. This is the second sentence.
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim strings() As String = { "This is the first sentence. ", 
                                  "This is the second sentence. " }
      Dim asciiEncoding As Encoding = Encoding.ASCII

      ' Create array of adequate size.
      Dim bytes(50) As Byte
      ' Create index for current position of array.
      Dim index As Integer = 0

      Console.WriteLine("Strings to encode:")
      For Each stringValue In strings
         Console.WriteLine("   {0}", stringValue)

         Dim count As Integer = asciiEncoding.GetByteCount(stringValue)
         If count + index >=  bytes.Length Then
            Array.Resize(bytes, bytes.Length + 50)
         End If
         Dim written As Integer = asciiEncoding.GetBytes(stringValue, 0, 
                                                         stringValue.Length, 
                                                         bytes, index)    

         index = index + written 
      Next 
      Console.WriteLine()
      Console.WriteLine("Encoded bytes:")
      Console.WriteLine("{0}", ShowByteValues(bytes, index))
      Console.WriteLine()

      ' Decode Unicode byte array to a string.
      Dim newString As String = asciiEncoding.GetString(bytes, 0, index)
      Console.WriteLine("Decoded: {0}", newString)
   End Sub

   Private Function ShowByteValues(bytes As Byte(), last As Integer) As String
      Dim returnString As String = "   "
      For ctr As Integer = 0 To last - 1
         If ctr Mod 20 = 0 Then returnString += vbCrLf + "   "
         returnString += String.Format("{0:X2} ", bytes(ctr))
      Next
      Return returnString
   End Function
End Module
' The example displays the following output:
'       Strings to encode:
'          This is the first sentence.
'          This is the second sentence.
'       
'       Encoded bytes:
'       
'          54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
'          6E 74 65 6E 63 65 2E 20 54 68 69 73 20 69 73 20 74 68 65 20
'          73 65 63 6F 6E 64 20 73 65 6E 74 65 6E 63 65 2E 20
'       
'       Decoded: This is the first sentence. This is the second sentence.
```

<span data-ttu-id="f9f27-222">Un décodeur convertit un tableau d'octets qui reflète un encodage de caractères spécifique en un jeu de caractères dans un tableau de caractères ou dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="f9f27-222">A decoder converts a byte array that reflects a particular character encoding into a set of characters, either in a character array or in a string.</span></span> <span data-ttu-id="f9f27-223">Pour décoder un tableau d’octets en tableau de caractères, vous appelez la méthode [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])).</span><span class="sxs-lookup"><span data-stu-id="f9f27-223">To decode a byte array into a character array, you call the [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) method.</span></span> <span data-ttu-id="f9f27-224">Pour décoder un tableau d’octets en chaîne, vous appelez la méthode [GetString](xref:System.Text.Encoding.GetString(System.Byte[])).</span><span class="sxs-lookup"><span data-stu-id="f9f27-224">To decode a byte array into a string, you call the [GetString](xref:System.Text.Encoding.GetString(System.Byte[])) method.</span></span> <span data-ttu-id="f9f27-225">Pour déterminer le nombre d’octets nécessaires pour stocker les caractères décodés avant de procéder au décodage, vous pouvez appeler la méthode [GetCharCount](xref:System.Text.Encoding.GetCharCount(System.Byte[])).</span><span class="sxs-lookup"><span data-stu-id="f9f27-225">If you want to determine how many characters are needed to store the decoded bytes before performing the decoding, you can call the [GetCharCount](xref:System.Text.Encoding.GetCharCount(System.Byte[])) method.</span></span>

<span data-ttu-id="f9f27-226">L'exemple suivant encode trois chaînes, puis les décode dans un même tableau de caractères.</span><span class="sxs-lookup"><span data-stu-id="f9f27-226">The following example encodes three strings and then decodes them into a single array of characters.</span></span> <span data-ttu-id="f9f27-227">Il gère un index qui indique la position de départ dans le tableau de caractères pour l'ensemble suivant de caractères décodés.</span><span class="sxs-lookup"><span data-stu-id="f9f27-227">It maintains an index that indicates the starting position in the character array for the next set of decoded characters.</span></span> <span data-ttu-id="f9f27-228">Il appelle la méthode [GetCharCount](xref:System.Text.Encoding.GetCharCount(System.Byte[])) pour vérifier que le tableau de caractères est assez grand pour contenir les caractères décodés.</span><span class="sxs-lookup"><span data-stu-id="f9f27-228">It calls the [GetCharCount](xref:System.Text.Encoding.GetCharCount(System.Byte[])) method to ensure that the character array is large enough to accommodate all the decoded characters.</span></span> <span data-ttu-id="f9f27-229">Il appelle ensuite la méthode [ASCIIEncoding.GetChars(Byte[], Int32, Int32, Char[], Int32)](xref:System.Text.ASCIIEncoding.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) pour décoder le tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="f9f27-229">It then calls the [ASCIIEncoding.GetChars(Byte[], Int32, Int32, Char[], Int32)](xref:System.Text.ASCIIEncoding.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) method to decode the byte array.</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      string[] strings = { "This is the first sentence. ", 
                           "This is the second sentence. ",
                           "This is the third sentence. " };
      Encoding asciiEncoding = Encoding.ASCII;
      // Array to hold encoded bytes.
      byte[] bytes;
      // Array to hold decoded characters.
      char[] chars = new char[50];
      // Create index for current position of character array.
      int index = 0;     

      foreach (var stringValue in strings) {
         Console.WriteLine("String to Encode: {0}", stringValue);
         // Encode the string to a byte array.
         bytes = asciiEncoding.GetBytes(stringValue);
         // Display the encoded bytes.
         Console.Write("Encoded bytes: ");
         for (int ctr = 0; ctr < bytes.Length; ctr++)
            Console.Write(" {0}{1:X2}", 
                          ctr % 20 == 0 ? Environment.NewLine : "", 
                          bytes[ctr]);
         Console.WriteLine();

         // Decode the bytes to a single character array.
         int count = asciiEncoding.GetCharCount(bytes);
         if (count + index >=  chars.Length)
            Array.Resize(ref chars, chars.Length + 50);

         int written = asciiEncoding.GetChars(bytes, 0, 
                                              bytes.Length, 
                                              chars, index);              
         index = index + written;
         Console.WriteLine();       
      }

      // Instantiate a single string containing the characters.
      string decodedString = new string(chars, 0, index - 1);
      Console.WriteLine("Decoded string: ");
      Console.WriteLine(decodedString);
   }
}
// The example displays the following output:
//    String to Encode: This is the first sentence.
//    Encoded bytes:
//    54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
//    6E 74 65 6E 63 65 2E 20
//    
//    String to Encode: This is the second sentence.
//    Encoded bytes:
//    54 68 69 73 20 69 73 20 74 68 65 20 73 65 63 6F 6E 64 20 73
//    65 6E 74 65 6E 63 65 2E 20
//    
//    String to Encode: This is the third sentence.
//    Encoded bytes:
//    54 68 69 73 20 69 73 20 74 68 65 20 74 68 69 72 64 20 73 65
//    6E 74 65 6E 63 65 2E 20
//    
//    Decoded string:
//    This is the first sentence. This is the second sentence. This is the third sentence.
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim strings() As String = { "This is the first sentence. ", 
                                  "This is the second sentence. ",
                                  "This is the third sentence. " }
      Dim asciiEncoding As Encoding = Encoding.ASCII
      ' Array to hold encoded bytes.
      Dim bytes() As Byte
      ' Array to hold decoded characters.
      Dim chars(50) As Char
      ' Create index for current position of character array.
      Dim index As Integer     

      For Each stringValue In strings
         Console.WriteLine("String to Encode: {0}", stringValue)
         ' Encode the string to a byte array.
         bytes = asciiEncoding.GetBytes(stringValue)
         ' Display the encoded bytes.
         Console.Write("Encoded bytes: ")
         For ctr As Integer = 0 To bytes.Length - 1
            Console.Write(" {0}{1:X2}", If(ctr Mod 20 = 0, vbCrLf, ""), 
                                        bytes(ctr))
         Next         
         Console.WriteLine()

         ' Decode the bytes to a single character array.
         Dim count As Integer = asciiEncoding.GetCharCount(bytes)
         If count + index >=  chars.Length Then
            Array.Resize(chars, chars.Length + 50)
         End If
         Dim written As Integer = asciiEncoding.GetChars(bytes, 0, 
                                                         bytes.Length, 
                                                         chars, index)              
         index = index + written
         Console.WriteLine()       
      Next

      ' Instantiate a single string containing the characters.
      Dim decodedString As New String(chars, 0, index - 1)
      Console.WriteLine("Decoded string: ")
      Console.WriteLine(decodedString)
   End Sub
End Module
' The example displays the following output:
'    String to Encode: This is the first sentence.
'    Encoded bytes:
'    54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
'    6E 74 65 6E 63 65 2E 20
'    
'    String to Encode: This is the second sentence.
'    Encoded bytes:
'    54 68 69 73 20 69 73 20 74 68 65 20 73 65 63 6F 6E 64 20 73
'    65 6E 74 65 6E 63 65 2E 20
'    
'    String to Encode: This is the third sentence.
'    Encoded bytes:
'    54 68 69 73 20 69 73 20 74 68 65 20 74 68 69 72 64 20 73 65
'    6E 74 65 6E 63 65 2E 20
'    
'    Decoded string:
'    This is the first sentence. This is the second sentence. This is the third sentence.
```

<span data-ttu-id="f9f27-230">Les méthodes d’encodage et de décodage d’une classe dérivée de [Encoding](xref:System.Text.Encoding) sont conçues pour fonctionner sur un ensemble de données complet ; autrement dit, toutes les données à encoder ou à décoder sont fournies dans un seul appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="f9f27-230">The encoding and decoding methods of a class derived from [Encoding](xref:System.Text.Encoding) are designed to work on a complete set of data; that is, all the data to be encoded or decoded is supplied in a single method call.</span></span> <span data-ttu-id="f9f27-231">Cependant, dans certains cas, les données sont disponibles dans un flux, et les données à encoder ou à décoder peuvent être disponibles seulement via des opérations de lecture distinctes.</span><span class="sxs-lookup"><span data-stu-id="f9f27-231">However, in some cases, data is available in a stream, and the data to be encoded or decoded may be available only from separate read operations.</span></span> <span data-ttu-id="f9f27-232">Ceci nécessite la conservation par l'opération d'encodage ou de décodage des états enregistrés depuis son précédent appel.</span><span class="sxs-lookup"><span data-stu-id="f9f27-232">This requires the encoding or decoding operation to remember any saved state from its previous invocation.</span></span> <span data-ttu-id="f9f27-233">Les méthodes des classes dérivées d’[Encoder](xref:System.Text.Encoder) et de [Decoder](xref:System.Text.Decoder) sont capables de traiter les opérations de codage et de décodage qui recouvrent plusieurs appels de méthode.</span><span class="sxs-lookup"><span data-stu-id="f9f27-233">Methods of classes derived from [Encoder](xref:System.Text.Encoder) and [Decoder](xref:System.Text.Decoder) are able to handle encoding and decoding operations that span multiple method calls.</span></span>

<span data-ttu-id="f9f27-234">Un objet [Encoder](xref:System.Text.Encoder) est disponible pour un encodage particulier à partir de la propriété [Encoding.GetEncoder](xref:System.Text.Encoding.GetEncoder) de cet encodage.</span><span class="sxs-lookup"><span data-stu-id="f9f27-234">An [Encoder](xref:System.Text.Encoder) object for a particular encoding is available from that encoding's [Encoding.GetEncoder](xref:System.Text.Encoding.GetEncoder) property.</span></span> <span data-ttu-id="f9f27-235">Un objet [Decoder](xref:System.Text.Decoder) est disponible pour un encodage particulier à partir de la propriété [Encoding.GetDecoder](xref:System.Text.Encoding.GetDecoder) de cet encodage.</span><span class="sxs-lookup"><span data-stu-id="f9f27-235">A [Decoder](xref:System.Text.Decoder) object for a particular encoding is available from that encoding's [Encoding.GetDecoder](xref:System.Text.Encoding.GetDecoder) property.</span></span> <span data-ttu-id="f9f27-236">Pour les opérations de décodage, notez que les classes dérivées de [Decoder](xref:System.Text.Decoder) incluent une méthode [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)), mais qu’elles n’ont pas de méthode qui correspond à [Encoding.GetString](xref:System.Text.Encoding.GetString(System.Byte[])).</span><span class="sxs-lookup"><span data-stu-id="f9f27-236">For decoding operations, note that classes derived from [Decoder](xref:System.Text.Decoder) include a [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) method, but they do not have a method that corresponds to [Encoding.GetString](xref:System.Text.Encoding.GetString(System.Byte[])).</span></span>

<span data-ttu-id="f9f27-237">L’exemple suivant montre la différence entre l’utilisation des méthodes [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) et [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) pour le décodage d’un tableau d’octets Unicode.</span><span class="sxs-lookup"><span data-stu-id="f9f27-237">The following example illustrates the difference between using the [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) and [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) methods for decoding a Unicode byte array.</span></span> <span data-ttu-id="f9f27-238">L'exemple encode une chaîne qui contient des caractères Unicode vers un fichier, puis utilise les deux méthodes de décodage pour les décoder par dix octets à la fois.</span><span class="sxs-lookup"><span data-stu-id="f9f27-238">The example encodes a string that contains some Unicode characters to a file, and then uses the two decoding methods to decode them ten bytes at a time.</span></span> <span data-ttu-id="f9f27-239">Une paire de substitution se trouvant dans les dixième et onzième octets, elle est décodée dans des appels de méthode distincts.</span><span class="sxs-lookup"><span data-stu-id="f9f27-239">Because a surrogate pair occurs in the tenth and eleventh bytes, it is decoded in separate method calls.</span></span> <span data-ttu-id="f9f27-240">Comme la sortie le montre, la méthode [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) ne peut pas décoder correctement les octets et les remplace par U+FFFD (CARACTÈRE DE REMPLACEMENT).</span><span class="sxs-lookup"><span data-stu-id="f9f27-240">As the output shows, the [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) method is not able to correctly decode the bytes and instead replaces them with U+FFFD (REPLACEMENT CHARACTER).</span></span> <span data-ttu-id="f9f27-241">En revanche, la méthode [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) peut décoder correctement le tableau d’octets pour obtenir la chaîne d’origine.</span><span class="sxs-lookup"><span data-stu-id="f9f27-241">On the other hand, the [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) method is able to successfully decode the byte array to get the original string.</span></span>

```csharp
using System;
using System.IO;
using System.Text;

public class Example
{
   public static void Main()
   {
      // Use default replacement fallback for invalid encoding.
      UnicodeEncoding enc = new UnicodeEncoding(true, false, false);

      // Define a string with various Unicode characters.
      string str1 = "AB YZ 19 \uD800\udc05 \u00e4"; 
      str1 += "Unicode characters. \u00a9 \u010C s \u0062\u0308"; 
      Console.WriteLine("Created original string...\n");

      // Convert string to byte array.                     
      byte[] bytes = enc.GetBytes(str1);

      FileStream fs = File.Create(@".\characters.bin");
      BinaryWriter bw = new BinaryWriter(fs);
      bw.Write(bytes);
      bw.Close();

      // Read bytes from file.
      FileStream fsIn = File.OpenRead(@".\characters.bin");
      BinaryReader br = new BinaryReader(fsIn);

      const int count = 10;            // Number of bytes to read at a time. 
      byte[] bytesRead = new byte[10]; // Buffer (byte array).
      int read;                        // Number of bytes actually read. 
      string str2 = String.Empty;      // Decoded string.

      // Try using Encoding object for all operations.
      do { 
         read = br.Read(bytesRead, 0, count);
         str2 += enc.GetString(bytesRead, 0, read); 
      } while (read == count);
      br.Close();
      Console.WriteLine("Decoded string using UnicodeEncoding.GetString()...");
      CompareForEquality(str1, str2);
      Console.WriteLine();

      // Use Decoder for all operations.
      fsIn = File.OpenRead(@".\characters.bin");
      br = new BinaryReader(fsIn);
      Decoder decoder = enc.GetDecoder();
      char[] chars = new char[50];
      int index = 0;                   // Next character to write in array.
      int written = 0;                 // Number of chars written to array.
      do { 
         read = br.Read(bytesRead, 0, count);
         if (index + decoder.GetCharCount(bytesRead, 0, read) - 1 >= chars.Length) 
            Array.Resize(ref chars, chars.Length + 50);

         written = decoder.GetChars(bytesRead, 0, read, chars, index);
         index += written;                          
      } while (read == count);
      br.Close();            
      // Instantiate a string with the decoded characters.
      string str3 = new String(chars, 0, index); 
      Console.WriteLine("Decoded string using UnicodeEncoding.Decoder.GetString()...");
      CompareForEquality(str1, str3); 
   }

   private static void CompareForEquality(string original, string decoded)
   {
      bool result = original.Equals(decoded);
      Console.WriteLine("original = decoded: {0}", 
                        original.Equals(decoded, StringComparison.Ordinal));
      if (! result) {
         Console.WriteLine("Code points in original string:");
         foreach (var ch in original)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));
         Console.WriteLine();

         Console.WriteLine("Code points in decoded string:");
         foreach (var ch in decoded)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));
         Console.WriteLine();
      }
   }
}
// The example displays the following output:
//    Created original string...
//    
//    Decoded string using UnicodeEncoding.GetString()...
//    original = decoded: False
//    Code points in original string:
//    0041 0042 0020 0059 005A 0020 0031 0039 0020 D800 DC05 0020 00E4 0055 006E 0069 0063 006F
//    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
//    0020 0073 0020 0062 0308
//    Code points in decoded string:
//    0041 0042 0020 0059 005A 0020 0031 0039 0020 FFFD FFFD 0020 00E4 0055 006E 0069 0063 006F
//    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
//    0020 0073 0020 0062 0308
//    
//    Decoded string using UnicodeEncoding.Decoder.GetString()...
//    original = decoded: True
```

```vb
Imports System.IO
Imports System.Text

Module Example
   Public Sub Main()
      ' Use default replacement fallback for invalid encoding.
      Dim enc As New UnicodeEncoding(True, False, False)

      ' Define a string with various Unicode characters.
      Dim str1 As String = String.Format("AB YZ 19 {0}{1} {2}", 
                                         ChrW(&hD800), ChrW(&hDC05), ChrW(&h00e4))
      str1 += String.Format("Unicode characters. {0} {1} s {2}{3}", 
                            ChrW(&h00a9), ChrW(&h010C), ChrW(&h0062), ChrW(&h0308))
      Console.WriteLine("Created original string...")
      Console.WriteLine()

      ' Convert string to byte array.                     
      Dim bytes() As Byte = enc.GetBytes(str1)

      Dim fs As FileStream = File.Create(".\characters.bin")
      Dim bw As New BinaryWriter(fs)
      bw.Write(bytes)
      bw.Close()

      ' Read bytes from file.
      Dim fsIn As FileStream = File.OpenRead(".\characters.bin")
      Dim br As New BinaryReader(fsIn)

      Const count As Integer = 10      ' Number of bytes to read at a time. 
      Dim bytesRead(9) As Byte         ' Buffer (byte array).
      Dim read As Integer              ' Number of bytes actually read. 
      Dim str2 As String = ""          ' Decoded string.

      ' Try using Encoding object for all operations.
      Do 
         read = br.Read(bytesRead, 0, count)
         str2 += enc.GetString(bytesRead, 0, read) 
      Loop While read = count
      br.Close()
      Console.WriteLine("Decoded string using UnicodeEncoding.GetString()...")
      CompareForEquality(str1, str2)
      Console.WriteLine()

      ' Use Decoder for all operations.
      fsIn = File.OpenRead(".\characters.bin")
      br = New BinaryReader(fsIn)
      Dim decoder As Decoder = enc.GetDecoder()
      Dim chars(50) As Char
      Dim index As Integer = 0         ' Next character to write in array.
      Dim written As Integer = 0       ' Number of chars written to array.
      Do 
         read = br.Read(bytesRead, 0, count)
         If index + decoder.GetCharCount(bytesRead, 0, read) - 1 >= chars.Length Then 
            Array.Resize(chars, chars.Length + 50)
         End If   
         written = decoder.GetChars(bytesRead, 0, read, chars, index)
         index += written                          
      Loop While read = count
      br.Close()            
      ' Instantiate a string with the decoded characters.
      Dim str3 As New String(chars, 0, index) 
      Console.WriteLine("Decoded string using UnicodeEncoding.Decoder.GetString()...")
      CompareForEquality(str1, str3) 
   End Sub

   Private Sub CompareForEquality(original As String, decoded As String)
      Dim result As Boolean = original.Equals(decoded)
      Console.WriteLine("original = decoded: {0}", 
                        original.Equals(decoded, StringComparison.Ordinal))
      If Not result Then
         Console.WriteLine("Code points in original string:")
         For Each ch In original
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
         Console.WriteLine()

         Console.WriteLine("Code points in decoded string:")
         For Each ch In decoded
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
         Console.WriteLine()
      End If
   End Sub
End Module
' The example displays the following output:
'    Created original string...
'    
'    Decoded string using UnicodeEncoding.GetString()...
'    original = decoded: False
'    Code points in original string:
'    0041 0042 0020 0059 005A 0020 0031 0039 0020 D800 DC05 0020 00E4 0055 006E 0069 0063 006F
'    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
'    0020 0073 0020 0062 0308
'    Code points in decoded string:
'    0041 0042 0020 0059 005A 0020 0031 0039 0020 FFFD FFFD 0020 00E4 0055 006E 0069 0063 006F
'    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
'    0020 0073 0020 0062 0308
'    
'    Decoded string using UnicodeEncoding.Decoder.GetString()...
'    original = decoded: True
```

## <a name="choosing-a-fallback-strategy"></a><span data-ttu-id="f9f27-242">Choix d’une stratégie de secours</span><span class="sxs-lookup"><span data-stu-id="f9f27-242">Choosing a fallback strategy</span></span>

<span data-ttu-id="f9f27-243">Quand une méthode tente d'encoder ou de décoder un caractère, mais qu'il n'existe pas de mappage, elle doit implémenter une stratégie de secours qui détermine comment l'échec du mappage doit être traité.</span><span class="sxs-lookup"><span data-stu-id="f9f27-243">When a method tries to encode or decode a character but no mapping exists, it must implement a fallback strategy that determines how the failed mapping should be handled.</span></span> <span data-ttu-id="f9f27-244">Il existe trois types de stratégies de secours :</span><span class="sxs-lookup"><span data-stu-id="f9f27-244">There are three types of fallback strategies:</span></span> 

* <span data-ttu-id="f9f27-245">Stratégie de secours la mieux adaptée</span><span class="sxs-lookup"><span data-stu-id="f9f27-245">Best-fit fallback</span></span>

* <span data-ttu-id="f9f27-246">Stratégie de secours pour les remplacements</span><span class="sxs-lookup"><span data-stu-id="f9f27-246">Replacement fallback</span></span>

* <span data-ttu-id="f9f27-247">Stratégie de secours pour les exceptions</span><span class="sxs-lookup"><span data-stu-id="f9f27-247">Exception fallback</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9f27-248">Les problèmes les plus courants des opérations d'encodage se produisent quand un caractère Unicode ne peut pas être mappé à un encodage de page de codes particulier.</span><span class="sxs-lookup"><span data-stu-id="f9f27-248">The most common problems in encoding operations occur when a Unicode character cannot be mapped to a particular code page encoding.</span></span> <span data-ttu-id="f9f27-249">Les problèmes les plus courants des opérations de décodage se produisent quand des séquences d'octets non valides ne peut pas être traduites en caractères Unicode valides.</span><span class="sxs-lookup"><span data-stu-id="f9f27-249">The most common problems in decoding operations occur when invalid byte sequences cannot be translated into valid Unicode characters.</span></span> <span data-ttu-id="f9f27-250">Pour ces raisons, vous devez savoir quelle stratégie de secours est utilisée par un objet de codage particulier.</span><span class="sxs-lookup"><span data-stu-id="f9f27-250">For these reasons, you should know which fallback strategy a particular encoding object uses.</span></span> <span data-ttu-id="f9f27-251">Chaque fois que c'est possible, vous devez spécifier la stratégie de secours utilisée par un objet d'encodage quand vous instanciez l'objet.</span><span class="sxs-lookup"><span data-stu-id="f9f27-251">Whenever possible, you should specify the fallback strategy used by an encoding object when you instantiate the object.</span></span>
 
### <a name="best-fit-fallback"></a><span data-ttu-id="f9f27-252">Stratégie de secours la mieux adaptée</span><span class="sxs-lookup"><span data-stu-id="f9f27-252">Best-fit fallback</span></span>

<span data-ttu-id="f9f27-253">Quand un caractère n'a pas de correspondance exacte dans l'encodage cible, l'encodeur peut essayer de le mapper à un caractère similaire.</span><span class="sxs-lookup"><span data-stu-id="f9f27-253">When a character does not have an exact match in the target encoding, the encoder can try to map it to a similar character.</span></span> <span data-ttu-id="f9f27-254">(La stratégie de secours la mieux adaptée est principalement un codage plutôt qu'un problème de décodage.</span><span class="sxs-lookup"><span data-stu-id="f9f27-254">(Best-fit fallback is mostly an encoding rather than a decoding issue.</span></span> <span data-ttu-id="f9f27-255">Il existe très peu de pages de codes contenant des caractères qui ne peuvent pas être mappés à Unicode.) La stratégie de secours la mieux adaptée correspond aux valeurs par défaut des encodages de pages de codes et de jeux de caractères codés sur deux octets, qui sont récupérés par les surcharges [Encoding.GetEncoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) et [Encoding.GetEncoding(String)](xref:System.Text.Encoding.GetEncoding(System.String)).</span><span class="sxs-lookup"><span data-stu-id="f9f27-255">There are very few code pages that contain characters that cannot be successfully mapped to Unicode.) Best-fit fallback is the default for code page and double-byte character set encodings that are retrieved by the [Encoding.GetEncoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) and [Encoding.GetEncoding(String)](xref:System.Text.Encoding.GetEncoding(System.String)) overloads.</span></span>

> [!NOTE]
> <span data-ttu-id="f9f27-256">En théorie, les classes d’encodage Unicode fournies dans .NET ([UTF8Encoding](xref:System.Text.UTF8Encoding), [UnicodeEncoding](xref:System.Text.UnicodeEncoding) et [UTF32Encoding](xref:System.Text.UTF32Encoding)) prennent en charge tous les caractères de tous les jeux de caractères : elles peuvent donc être utilisées pour éliminer les problèmes liés à la stratégie de secours la mieux adaptée.</span><span class="sxs-lookup"><span data-stu-id="f9f27-256">In theory, the Unicode encoding classes provided in .NET ([UTF8Encoding](xref:System.Text.UTF8Encoding), [UnicodeEncoding](xref:System.Text.UnicodeEncoding), and [UTF32Encoding](xref:System.Text.UTF32Encoding)) support every character in every character set, so they can be used to eliminate best-fit fallback issues.</span></span> 
 

<span data-ttu-id="f9f27-257">Les stratégies de secours les mieux adaptées varient pour les différentes pages de code et elles ne sont pas documentées en détail.</span><span class="sxs-lookup"><span data-stu-id="f9f27-257">Best-fit strategies vary for different code pages, and they are not documented in detail.</span></span> <span data-ttu-id="f9f27-258">Par exemple, pour certaines pages de codes, les caractères latins à pleine chasse sont mappés aux caractères latins à demi-chasse plus courants.</span><span class="sxs-lookup"><span data-stu-id="f9f27-258">For example, for some code pages, full-width Latin characters map to the more common half-width Latin characters.</span></span> <span data-ttu-id="f9f27-259">Pour d'autres pages de codes, ce mappage n'est pas effectué.</span><span class="sxs-lookup"><span data-stu-id="f9f27-259">For other code pages, this mapping is not made.</span></span> <span data-ttu-id="f9f27-260">Même avec une stratégie la plus adaptée appliquée de façon agressive, il n'existe pas d'ajustement possible pour certains caractères dans certains encodages.</span><span class="sxs-lookup"><span data-stu-id="f9f27-260">Even under an aggressive best-fit strategy, there is no imaginable fit for some characters in some encodings.</span></span> <span data-ttu-id="f9f27-261">Par exemple, un idéogramme chinois n'a pas de mappage acceptable avec la page de codes 1252.</span><span class="sxs-lookup"><span data-stu-id="f9f27-261">For example, a Chinese ideograph has no reasonable mapping to code page 1252.</span></span> <span data-ttu-id="f9f27-262">Dans ce cas, une chaîne de remplacement est utilisée.</span><span class="sxs-lookup"><span data-stu-id="f9f27-262">In this case, a replacement string is used.</span></span> <span data-ttu-id="f9f27-263">Par défaut, cette chaîne est simplement un POINT D'INTERROGATION (U+003F).</span><span class="sxs-lookup"><span data-stu-id="f9f27-263">By default, this string is just a single QUESTION MARK (U+003F).</span></span>

<span data-ttu-id="f9f27-264">L'exemple suivant utilise la page de codes 1252 (la page de codes Windows pour les langues d'Europe occidentale) pour illustrer le mappage le mieux adapté et ses inconvénients.</span><span class="sxs-lookup"><span data-stu-id="f9f27-264">The following example uses code page 1252 (the Windows code page for Western European languages) to illustrate best-fit mapping and its drawbacks.</span></span> <span data-ttu-id="f9f27-265">La méthode [Encoding.GetEncoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) est utilisée pour récupérer un objet d’encodage pour la page de codes 1252.</span><span class="sxs-lookup"><span data-stu-id="f9f27-265">The [Encoding.GetEncoding(Int32](xref:System.Text.Encoding.GetEncoding(System.Int32)) method is used to retrieve an encoding object for code page 1252.</span></span> <span data-ttu-id="f9f27-266">Par défaut, elle utilise un mappage le mieux adapté pour les caractères Unicode qu'elle ne prend pas en charge.</span><span class="sxs-lookup"><span data-stu-id="f9f27-266">By default, it uses a best-fit mapping for Unicode characters that it does not support.</span></span> <span data-ttu-id="f9f27-267">L'exemple instancie une chaîne contenant trois caractères non-ASCII, LETTRE MAJUSCULE LATINE S CERCLÉE (U+24C8), EXPOSANT CINQ (U+2075) et INFINI (U+221E), séparés par des espaces.</span><span class="sxs-lookup"><span data-stu-id="f9f27-267">The example instantiates a string that contains three non-ASCII characters - CIRCLED LATIN CAPITAL LETTER S (U+24C8), SUPERSCRIPT FIVE (U+2075), and INFINITY (U+221E) - separated by spaces.</span></span> <span data-ttu-id="f9f27-268">Comme le montre la sortie de l'exemple, quand la chaîne est encodée, les trois caractères d'origine autres qu'un espace sont remplacés par POINT D'INTERROGATION (U+003F), CHIFFRE CINQ (U+0035) et CHIFFRE HUIT (U+0038).</span><span class="sxs-lookup"><span data-stu-id="f9f27-268">As the output from the example shows, when the string is encoded, the three original non-space characters are replaced by QUESTION MARK (U+003F), DIGIT FIVE (U+0035), and DIGIT EIGHT (U+0038).</span></span> <span data-ttu-id="f9f27-269">CHIFFRE HUIT est un substitut particulièrement médiocre pour le caractère INFINI non pris en charge, et POINT D'INTERROGATION indique qu'aucun mappage n'est disponible pour le caractère d'origine.</span><span class="sxs-lookup"><span data-stu-id="f9f27-269">DIGIT EIGHT is a particularly poor replacement for the unsupported INFINITY character, and QUESTION MARK indicates that no mapping was available for the original character.</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      // Get an encoding for code page 1252 (Western Europe character set).
      Encoding cp1252 = Encoding.GetEncoding(1252);

      // Define and display a string.
      string str = "\u24c8 \u2075 \u221e";
      Console.WriteLine("Original string: " + str);
      Console.Write("Code points in string: ");
      foreach (var ch in str)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine("\n");   

      // Encode a Unicode string.
      Byte[] bytes = cp1252.GetBytes(str);
      Console.Write("Encoded bytes: ");
      foreach (byte byt in bytes)
         Console.Write("{0:X2} ", byt);
      Console.WriteLine("\n");

      // Decode the string.
      string str2 = cp1252.GetString(bytes);
      Console.WriteLine("String round-tripped: {0}", str.Equals(str2));
      if (! str.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));
      }
   }
}
// The example displays the following output:
//       Original string: Ⓢ ⁵ ∞
//       Code points in string: 24C8 0020 2075 0020 221E
//       
//       Encoded bytes: 3F 20 35 20 38
//       
//       String round-tripped: False
//       ? 5 8
//       003F 0020 0035 0020 0038
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      ' Get an encoding for code page 1252 (Western Europe character set).
      Dim cp1252 As Encoding = Encoding.GetEncoding(1252)

      ' Define and display a string.
      Dim str As String = String.Format("{0} {1} {2}", ChrW(&h24c8), ChrW(&H2075), ChrW(&h221E))
      Console.WriteLine("Original string: " + str)
      Console.Write("Code points in string: ")
      For Each ch In str
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next
      Console.WriteLine()   
      Console.WriteLine()

      ' Encode a Unicode string.
      Dim bytes() As Byte = cp1252.GetBytes(str)
      Console.Write("Encoded bytes: ")
      For Each byt In bytes
         Console.Write("{0:X2} ", byt)
      Next
      Console.WriteLine()
      Console.WriteLine()

      ' Decode the string.
      Dim str2 As String = cp1252.GetString(bytes)
      Console.WriteLine("String round-tripped: {0}", str.Equals(str2))
      If Not str.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
      End If
   End Sub
End Module
' The example displays the following output:
'       Original string: Ⓢ ⁵ ∞
'       Code points in string: 24C8 0020 2075 0020 221E
'       
'       Encoded bytes: 3F 20 35 20 38
'       
'       String round-tripped: False
'       ? 5 8
'       003F 0020 0035 0020 0038
```

<span data-ttu-id="f9f27-270">Le mappage le mieux adapté est le comportement par défaut d’un objet [Encoding](xref:System.Text.Encoding) qui encode des données Unicode en données de page de codes, et il existe des applications héritées qui s’appuient sur ce comportement.</span><span class="sxs-lookup"><span data-stu-id="f9f27-270">Best-fit mapping is the default behavior for an [Encoding](xref:System.Text.Encoding) object that encodes Unicode data into code page data, and there are legacy applications that rely on this behavior.</span></span> <span data-ttu-id="f9f27-271">Cependant, la plupart des nouvelles applications doivent éviter ce comportement le mieux adapté pour des raisons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="f9f27-271">However, most new applications should avoid best-fit behavior for security reasons.</span></span> <span data-ttu-id="f9f27-272">Par exemple, les applications ne doivent pas établir un nom de domaine via un encodage le mieux adapté.</span><span class="sxs-lookup"><span data-stu-id="f9f27-272">For example, applications should not put a domain name through a best-fit encoding.</span></span>

> [!Note]
> <span data-ttu-id="f9f27-273">Vous pouvez également implémenter un mappage de stratégie de secours la mieux adaptée personnalisé pour un encodage.</span><span class="sxs-lookup"><span data-stu-id="f9f27-273">You can also implement a custom best-fit fallback mapping for an encoding.</span></span> <span data-ttu-id="f9f27-274">Pour plus d’informations, consultez la section [Implémentation d’une stratégie de secours personnalisée](#implementing-a-custom-fallback-strategy).</span><span class="sxs-lookup"><span data-stu-id="f9f27-274">For more information, see the [Implementing a custom fallback strategy](#implementing-a-custom-fallback-strategy) section.</span></span>
 
<span data-ttu-id="f9f27-275">Si la stratégie de secours la mieux adaptée est la valeur par défaut d’un objet d’encodage, vous pouvez choisir une autre stratégie de secours quand vous récupérez un objet [Encoding](xref:System.Text.Encoding) en appelant la surcharge [Encoding.GetEncoding(Int32, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)) ou [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)).</span><span class="sxs-lookup"><span data-stu-id="f9f27-275">If best-fit fallback is the default for an encoding object, you can choose another fallback strategy when you retrieve an [Encoding](xref:System.Text.Encoding) object by calling the [Encoding.GetEncoding(Int32, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)) or [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) overload.</span></span> <span data-ttu-id="f9f27-276">La section suivante contient un exemple qui remplace chaque caractère qui ne peut pas être mappé à la page de codes 1252 par un astérisque (\*).</span><span class="sxs-lookup"><span data-stu-id="f9f27-276">The following section includes an example that replaces each character that cannot be mapped to code page 1252 with an asterisk (\*).</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding cp1252r = Encoding.GetEncoding(1252, 
                                  new EncoderReplacementFallback("*"),
                                  new DecoderReplacementFallback("*"));

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine();

      byte[] bytes = cp1252r.GetBytes(str1);
      string str2 = cp1252r.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      } 
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       Round-trip: False
//       * * *
//       002A 0020 002A 0020 002A
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim cp1252r As Encoding = Encoding.GetEncoding(1252, 
                                         New EncoderReplacementFallback("*"),
                                         New DecoderReplacementFallback("*"))

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()

      Dim bytes() As Byte = cp1252r.GetBytes(str1)
      Dim str2 As String = cp1252r.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next    
         Console.WriteLine()
      End If 
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       Round-trip: False
'       * * *
'       002A 0020 002A 0020 002A
```

### <a name="replacement-fallback"></a><span data-ttu-id="f9f27-277">Stratégie de secours pour les remplacements</span><span class="sxs-lookup"><span data-stu-id="f9f27-277">Replacement fallback</span></span>

<span data-ttu-id="f9f27-278">Quand un caractère n'a pas de correspondance exacte dans le schéma cible, mais qu'il n'existe pas de caractère approprié auquel il peut être mappé, l'application peut spécifier un caractère ou une chaîne de remplacement.</span><span class="sxs-lookup"><span data-stu-id="f9f27-278">When a character does not have an exact match in the target scheme, but there is no appropriate character that it can be mapped to, the application can specify a replacement character or string.</span></span> <span data-ttu-id="f9f27-279">Il s'agit du comportement par défaut pour le décodeur Unicode, qui remplace toutes les séquences de deux octets qu'il ne peut pas décoder par CARACTÈRE_DE_REMPLACEMENT (U+FFFD).</span><span class="sxs-lookup"><span data-stu-id="f9f27-279">This is the default behavior for the Unicode decoder, which replaces any two-byte sequence that it cannot decode with REPLACEMENT_CHARACTER (U+FFFD).</span></span> <span data-ttu-id="f9f27-280">C’est également le comportement par défaut de la classe [ASCIIEncoding](xref:System.Text.ASCIIEncoding), qui remplace chaque caractère qu’elle ne peut pas encoder ou décoder par un point d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="f9f27-280">It is also the default behavior of the [ASCIIEncoding](xref:System.Text.ASCIIEncoding) class, which replaces each character that it cannot encode or decode with a question mark.</span></span> <span data-ttu-id="f9f27-281">L'exemple suivant illustre le remplacement de caractères pour la chaîne Unicode de l'exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="f9f27-281">The following example illustrates character replacement for the Unicode string from the previous example.</span></span> <span data-ttu-id="f9f27-282">Comme le montre la sortie, chaque caractère qui ne peut pas être décodé en une valeur d'octet ASCII est remplacé par 0x3F, qui est le code ASCII pour un point d'interrogation.</span><span class="sxs-lookup"><span data-stu-id="f9f27-282">As the output shows, each character that cannot be decoded into an ASCII byte value is replaced by 0x3F, which is the ASCII code for a question mark.</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding enc = Encoding.ASCII;

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine("\n");

      // Encode the original string using the ASCII encoder.
      byte[] bytes = enc.GetBytes(str1);
      Console.Write("Encoded bytes: ");
      foreach (var byt in bytes)
         Console.Write("{0:X2} ", byt);
      Console.WriteLine("\n");

      // Decode the ASCII bytes.
      string str2 = enc.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      } 
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       
//       Encoded bytes: 3F 20 3F 20 3F
//       
//       Round-trip: False
//       ? ? ?
//       003F 0020 003F 0020 003F
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim enc As Encoding = Encoding.Ascii

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()
      Console.WriteLine() 

      ' Encode the original string using the ASCII encoder.
      Dim bytes() As Byte = enc.GetBytes(str1)
      Console.Write("Encoded bytes: ")
      For Each byt In bytes
         Console.Write("{0:X2} ", byt)
      Next
      Console.WriteLine()
      Console.WriteLine()

      ' Decode the ASCII bytes.
      Dim str2 As String = enc.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next    
         Console.WriteLine()
      End If 
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       
'       Encoded bytes: 3F 20 3F 20 3F
'       
'       Round-trip: False
'       ? ? ?
'       003F 0020 003F 0020 003F
```

<span data-ttu-id="f9f27-283">.NET inclut les classes [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) et [DecoderReplacementFallback](xref:System.Text.DecoderReplacementFallback), qui substituent une chaîne de remplacement si un caractère ne correspond pas exactement dans une opération d’encodage ou de décodage.</span><span class="sxs-lookup"><span data-stu-id="f9f27-283">.NET includes the [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) and [DecoderReplacementFallback](xref:System.Text.DecoderReplacementFallback) classes, which substitute a replacement string if a character does not map exactly in an encoding or decoding operation.</span></span> <span data-ttu-id="f9f27-284">Par défaut, cette chaîne de remplacement est un point d'interrogation, mais vous pouvez appeler une surcharge de constructeur de classe pour choisir une autre chaîne.</span><span class="sxs-lookup"><span data-stu-id="f9f27-284">By default, this replacement string is a question mark, but you can call a class constructor overload to choose a different string.</span></span> <span data-ttu-id="f9f27-285">En général, la chaîne de remplacement est un caractère unique, même si ce n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="f9f27-285">Typically, the replacement string is a single character, although this is not a requirement.</span></span> <span data-ttu-id="f9f27-286">L’exemple suivant change le comportement de l’encodeur de la page de codes 1252 en instanciant un objet [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) qui utilise un astérisque (\*) comme chaîne de remplacement.</span><span class="sxs-lookup"><span data-stu-id="f9f27-286">The following example changes the behavior of the code page 1252 encoder by instantiating an [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) object that uses an asterisk (\*) as a replacement string.</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding cp1252r = Encoding.GetEncoding(1252, 
                                  new EncoderReplacementFallback("*"),
                                  new DecoderReplacementFallback("*"));

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine();

      byte[] bytes = cp1252r.GetBytes(str1);
      string str2 = cp1252r.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      } 
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       Round-trip: False
//       * * *
//       002A 0020 002A 0020 002A
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim cp1252r As Encoding = Encoding.GetEncoding(1252, 
                                         New EncoderReplacementFallback("*"),
                                         New DecoderReplacementFallback("*"))

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()

      Dim bytes() As Byte = cp1252r.GetBytes(str1)
      Dim str2 As String = cp1252r.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next    
         Console.WriteLine()
      End If 
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       Round-trip: False
'       * * *
'       002A 0020 002A 0020 002A
```

> [!NOTE]
> <span data-ttu-id="f9f27-287">Vous pouvez également implémenter une classe de remplacement pour un encodage.</span><span class="sxs-lookup"><span data-stu-id="f9f27-287">You can also implement a replacement class for an encoding.</span></span> <span data-ttu-id="f9f27-288">Pour plus d’informations, consultez la section [Implémentation d’une stratégie de secours personnalisée](#implementing-a-custom-fallback-strategy).</span><span class="sxs-lookup"><span data-stu-id="f9f27-288">For more information, see the [Implementing a custom fallback strategy](#implementing-a-custom-fallback-strategy) section.</span></span>
 
<span data-ttu-id="f9f27-289">En plus du POINT D'INTERROGATION (U+003F), le CARACTÈRE DE REMPLACEMENT Unicode (U+FFFD) est couramment utilisé comme chaîne de remplacement, en particulier lors du décodage de séquences d'octets qui ne peuvent pas être converties en caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="f9f27-289">In addition to QUESTION MARK (U+003F), the Unicode REPLACEMENT CHARACTER (U+FFFD) is commonly used as a replacement string, particularly when decoding byte sequences that cannot be successfully translated into Unicode characters.</span></span> <span data-ttu-id="f9f27-290">Vous êtes cependant libre de choisir n'importe quelle chaîne de remplacement, qui peut contenir plusieurs caractères.</span><span class="sxs-lookup"><span data-stu-id="f9f27-290">However, you are free to choose any replacement string, and it can contain multiple characters.</span></span>

### <a name="exception-fallback"></a><span data-ttu-id="f9f27-291">Stratégie de secours pour les exceptions</span><span class="sxs-lookup"><span data-stu-id="f9f27-291">Exception fallback</span></span>

<span data-ttu-id="f9f27-292">Au lieu de fournir une stratégie de secours la mieux adaptée ou une chaîne de remplacement, un encodeur peut lever une exception [EncoderFallbackException](xref:System.Text.EncoderFallbackException) s’il ne peut pas encoder un jeu de caractères, et un décodeur peut lever une exception [DecoderFallbackException](xref:System.Text.DecoderFallbackException) s’il ne peut pas décoder un tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="f9f27-292">Instead of providing a best-fit fallback or a replacement string, an encoder can throw an [EncoderFallbackException](xref:System.Text.EncoderFallbackException) if it is unable to encode a set of characters, and a decoder can throw a [DecoderFallbackException](xref:System.Text.DecoderFallbackException) if it is unable to decode a byte array.</span></span> <span data-ttu-id="f9f27-293">Pour lever une exception dans les opérations d’encodage et de décodage, vous fournissez respectivement un objet [EncoderFallbackException](xref:System.Text.EncoderFallbackException) et un objet [DecoderFallbackException](xref:System.Text.DecoderFallbackException) à la méthode [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)).</span><span class="sxs-lookup"><span data-stu-id="f9f27-293">To throw an exception in encoding and decoding operations, you supply an [EncoderFallbackException](xref:System.Text.EncoderFallbackException) object and a [DecoderFallbackException](xref:System.Text.DecoderFallbackException) object, respectively, to the [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) method.</span></span> <span data-ttu-id="f9f27-294">L’exemple suivant montre la stratégie de secours pour les exceptions avec la classe ASCIIEncoding.</span><span class="sxs-lookup"><span data-stu-id="f9f27-294">The following example illustrates exception fallback with the ASCIIEncoding class.</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding enc = Encoding.GetEncoding("us-ascii", 
                                          new EncoderExceptionFallback(), 
                                          new DecoderExceptionFallback());

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine("\n");

      // Encode the original string using the ASCII encoder.
      byte[] bytes = {};
      try {
         bytes = enc.GetBytes(str1);
         Console.Write("Encoded bytes: ");
         foreach (var byt in bytes)
            Console.Write("{0:X2} ", byt);

         Console.WriteLine();
      }
      catch (EncoderFallbackException e) {
         Console.Write("Exception: ");
         if (e.IsUnknownSurrogate())
            Console.WriteLine("Unable to encode surrogate pair 0x{0:X4} 0x{1:X3} at index {2}.", 
                              Convert.ToUInt16(e.CharUnknownHigh), 
                              Convert.ToUInt16(e.CharUnknownLow), 
                              e.Index);
         else
            Console.WriteLine("Unable to encode 0x{0:X4} at index {1}.", 
                              Convert.ToUInt16(e.CharUnknown), 
                              e.Index);
         return;
      }
      Console.WriteLine();

      // Decode the ASCII bytes.
      try {
         string str2 = enc.GetString(bytes);
         Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
         if (! str1.Equals(str2)) {
            Console.WriteLine(str2);
            foreach (var ch in str2)
               Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

            Console.WriteLine();
         } 
      }
      catch (DecoderFallbackException e) {
         Console.Write("Unable to decode byte(s) ");
         foreach (byte unknown in e.BytesUnknown)
            Console.Write("0x{0:X2} ");

         Console.WriteLine("at index {0}", e.Index);
      }
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       
//       Exception: Unable to encode 0x24C8 at index 0.
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim enc As Encoding = Encoding.GetEncoding("us-ascii", 
                                                 New EncoderExceptionFallback(), 
                                                 New DecoderExceptionFallback())

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()
      Console.WriteLine() 

      ' Encode the original string using the ASCII encoder.
      Dim bytes() As Byte = {}
      Try
         bytes = enc.GetBytes(str1)
         Console.Write("Encoded bytes: ")
         For Each byt In bytes
            Console.Write("{0:X2} ", byt)
         Next
         Console.WriteLine()
      Catch e As EncoderFallbackException
         Console.Write("Exception: ")
         If e.IsUnknownSurrogate() Then
            Console.WriteLine("Unable to encode surrogate pair 0x{0:X4} 0x{1:X3} at index {2}.", 
                              Convert.ToUInt16(e.CharUnknownHigh), 
                              Convert.ToUInt16(e.CharUnknownLow), 
                              e.Index)
         Else
            Console.WriteLine("Unable to encode 0x{0:X4} at index {1}.", 
                              Convert.ToUInt16(e.CharUnknown), 
                              e.Index)
         End If                              
         Exit Sub
      End Try
      Console.WriteLine()

      ' Decode the ASCII bytes.
      Try
         Dim str2 As String = enc.GetString(bytes)
         Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
         If Not str1.Equals(str2) Then
            Console.WriteLine(str2)
            For Each ch In str2
               Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
            Next    
            Console.WriteLine()
         End If 
      Catch e As DecoderFallbackException
         Console.Write("Unable to decode byte(s) ")
         For Each unknown As Byte In e.BytesUnknown
            Console.Write("0x{0:X2} ")
         Next
         Console.WriteLine("at index {0}", e.Index)
      End Try
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       
'       Exception: Unable to encode 0x24C8 at index 0.
```

> [!NOTE]
> <span data-ttu-id="f9f27-295">Vous pouvez également implémenter un gestionnaire d'exceptions personnalisé pour une opération d'encodage.</span><span class="sxs-lookup"><span data-stu-id="f9f27-295">You can also implement a custom exception handler for an encoding operation.</span></span> <span data-ttu-id="f9f27-296">Pour plus d’informations, consultez la section [Implémentation d’une stratégie de secours personnalisée](#implementing-a-custom-fallback-strategy).</span><span class="sxs-lookup"><span data-stu-id="f9f27-296">For more information, see the [Implementing a custom fallback strategy](#implementing-a-custom-fallback-strategy) section.</span></span>
 
<span data-ttu-id="f9f27-297">Les objets [EncoderFallbackException](xref:System.Text.EncoderFallbackException) et [DecoderFallbackException](xref:System.Text.DecoderFallbackException) fournissent les informations suivantes sur la condition qui a provoqué l’exception :</span><span class="sxs-lookup"><span data-stu-id="f9f27-297">The [EncoderFallbackException](xref:System.Text.EncoderFallbackException) and [DecoderFallbackException](xref:System.Text.DecoderFallbackException) objects provide the following information about the condition that caused the exception:</span></span> 

* <span data-ttu-id="f9f27-298">L’objet [EncoderFallbackException](xref:System.Text.EncoderFallbackException) comprend une méthode [IsUnknownSurrogate](xref:System.Text.EncoderFallbackException.IsUnknownSurrogate), qui indique si le ou les caractères qui ne peuvent pas être encodés représentent une paire de substitution inconnue (auquel cas la méthode retourne `true`) ou un seul caractère inconnu (auquel cas la méthode retourne `false`).</span><span class="sxs-lookup"><span data-stu-id="f9f27-298">The [EncoderFallbackException](xref:System.Text.EncoderFallbackException) object includes an [IsUnknownSurrogate](xref:System.Text.EncoderFallbackException.IsUnknownSurrogate) method, which indicates whether the character or characters that cannot be encoded represent an unknown surrogate pair (in which case, the method returns `true`) or an unknown single character (in which case, the method returns `false`).</span></span> <span data-ttu-id="f9f27-299">Les caractères de la paire de substitution sont disponibles à partir des propriétés [EncoderFallbackException.CharUnknownHigh](xref:System.Text.EncoderFallbackException.CharUnknownHigh) et [EncoderFallbackException.CharUnknownLow](xref:System.Text.EncoderFallbackException.CharUnknownLow).</span><span class="sxs-lookup"><span data-stu-id="f9f27-299">The characters in the surrogate pair are available from the [EncoderFallbackException.CharUnknownHigh](xref:System.Text.EncoderFallbackException.CharUnknownHigh) and [EncoderFallbackException.CharUnknownLow](xref:System.Text.EncoderFallbackException.CharUnknownLow) properties.</span></span> <span data-ttu-id="f9f27-300">Le caractère unique inconnu est disponible à partir de la propriété [EncoderFallbackException.CharUnknown](xref:System.Text.EncoderFallbackException.CharUnknown).</span><span class="sxs-lookup"><span data-stu-id="f9f27-300">The unknown single character is available from the [EncoderFallbackException.CharUnknown](xref:System.Text.EncoderFallbackException.CharUnknown) property.</span></span> <span data-ttu-id="f9f27-301">La propriété [EncoderFallbackException.Index](xref:System.Text.EncoderFallbackException.Index) indique la position dans la chaîne du premier caractère qui n’a pas pu être encodé.</span><span class="sxs-lookup"><span data-stu-id="f9f27-301">The [EncoderFallbackException.Index](xref:System.Text.EncoderFallbackException.Index) property indicates the position in the string at which the first character that could not be encoded was found.</span></span>

* <span data-ttu-id="f9f27-302">L’objet [DecoderFallbackException](xref:System.Text.DecoderFallbackException) inclut une propriété [BytesUnknown](xref:System.Text.DecoderFallbackException.BytesUnknown) qui retourne un tableau d’octets qui ne peut pas être décodé.</span><span class="sxs-lookup"><span data-stu-id="f9f27-302">The [DecoderFallbackException](xref:System.Text.DecoderFallbackException) object includes a [BytesUnknown](xref:System.Text.DecoderFallbackException.BytesUnknown) property that returns an array of bytes that cannot be decoded.</span></span> <span data-ttu-id="f9f27-303">La propriété [DecoderFallbackException.Index](xref:System.Text.DecoderFallbackException.Index) indique la position de départ des octets inconnus.</span><span class="sxs-lookup"><span data-stu-id="f9f27-303">The [DecoderFallbackException.Index](xref:System.Text.DecoderFallbackException.Index) property indicates the starting position of the unknown bytes.</span></span>

<span data-ttu-id="f9f27-304">Bien que les objets [EncoderFallbackException](xref:System.Text.EncoderFallbackException) et [DecoderFallbackException](xref:System.Text.DecoderFallbackException) fournissent des informations de diagnostic adéquates sur l’exception, ils ne donnent pas accès à la mémoire tampon d’encodage ou de décodage.</span><span class="sxs-lookup"><span data-stu-id="f9f27-304">Although the [EncoderFallbackException](xref:System.Text.EncoderFallbackException) and [DecoderFallbackException](xref:System.Text.DecoderFallbackException) objects provide adequate diagnostic information about the exception, they do not provide access to the encoding or decoding buffer.</span></span> <span data-ttu-id="f9f27-305">Par conséquent, ils ne permettent pas le remplacement ou la correction des données non valides dans la méthode d'encodage ou de décodage.</span><span class="sxs-lookup"><span data-stu-id="f9f27-305">Therefore, they do not allow invalid data to be replaced or corrected within the encoding or decoding method.</span></span>

## <a name="implementing-a-custom-fallback-strategy"></a><span data-ttu-id="f9f27-306">Implémentation d’une stratégie de secours personnalisée</span><span class="sxs-lookup"><span data-stu-id="f9f27-306">Implementing a custom fallback strategy</span></span>

<span data-ttu-id="f9f27-307">En plus du mappage le mieux adapté implémenté en interne par les pages de codes, .NET comprend les classes suivantes pour l’implémentation d’une stratégie de secours :</span><span class="sxs-lookup"><span data-stu-id="f9f27-307">In addition to the best-fit mapping that is implemented internally by code pages, .NET includes the following classes for implementing a fallback strategy:</span></span>

* <span data-ttu-id="f9f27-308">Utilisez [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) et [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) pour remplacer des caractères dans des opérations d’encodage.</span><span class="sxs-lookup"><span data-stu-id="f9f27-308">Use [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) and [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) to replace characters in encoding operations.</span></span>

* <span data-ttu-id="f9f27-309">Utilisez [DecoderReplacementFallback](xref:System.Text.DecoderReplacementFallback) et [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) pour remplacer des caractères dans des opérations de décodage.</span><span class="sxs-lookup"><span data-stu-id="f9f27-309">Use [DecoderReplacementFallback](xref:System.Text.DecoderReplacementFallback) and [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) to replace characters in decoding operations.</span></span>

* <span data-ttu-id="f9f27-310">Utilisez [EncoderExceptionFallback](xref:System.Text.EncoderExceptionFallback) et [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) pour lever une exception [EncoderFallbackException](xref:System.Text.EncoderFallbackException) quand un caractère ne peut pas être encodé.</span><span class="sxs-lookup"><span data-stu-id="f9f27-310">Use [EncoderExceptionFallback](xref:System.Text.EncoderExceptionFallback) and [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) to throw an [EncoderFallbackException](xref:System.Text.EncoderFallbackException) when a character cannot be encoded.</span></span>

* <span data-ttu-id="f9f27-311">Utilisez [DecoderExceptionFallback](xref:System.Text.DecoderExceptionFallback) et [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) pour lever une exception [DecoderFallbackException](xref:System.Text.DecoderFallbackException) quand un caractère ne peut pas être décodé.</span><span class="sxs-lookup"><span data-stu-id="f9f27-311">Use [DecoderExceptionFallback](xref:System.Text.DecoderExceptionFallback) and [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) to throw a [DecoderFallbackException](xref:System.Text.DecoderFallbackException) when a character cannot be decoded.</span></span>

<span data-ttu-id="f9f27-312">En outre, vous pouvez implémenter une solution personnalisée qui utilise une stratégie de secours la mieux adaptée, une stratégie de secours pour les remplacements ou une stratégie de secours pour les exceptions, en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="f9f27-312">In addition, you can implement a custom solution that uses best-fit fallback, replacement fallback, or exception fallback, by following these steps:</span></span> 

1. <span data-ttu-id="f9f27-313">Dérivez une classe d’[EncoderFallback](xref:System.Text.EncoderFallback) pour les opérations d’encodage et de [DecoderFallback](xref:System.Text.DecoderFallback) pour les opérations de décodage.</span><span class="sxs-lookup"><span data-stu-id="f9f27-313">Derive a class from [EncoderFallback](xref:System.Text.EncoderFallback) for encoding operations, and from [DecoderFallback](xref:System.Text.DecoderFallback) for decoding operations.</span></span>

2. <span data-ttu-id="f9f27-314">Dérivez une classe d’[EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) pour les opérations d’encodage et de [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) pour les opérations de décodage.</span><span class="sxs-lookup"><span data-stu-id="f9f27-314">Derive a class from [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) for encoding operations, and from [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) for decoding operations.</span></span>

3. <span data-ttu-id="f9f27-315">Pour la stratégie de secours pour les exeptions, si les classes [EncoderFallbackException](xref:System.Text.EncoderFallbackException) et [DecoderFallbackException](xref:System.Text.DecoderFallbackException) ne répondent pas à vos besoins, dérivez une classe d’un objet d’exception comme [Exception](xref:System.Exception) ou [ArgumentException](xref:System.ArgumentException).</span><span class="sxs-lookup"><span data-stu-id="f9f27-315">For exception fallback, if the predefined [EncoderFallbackException](xref:System.Text.EncoderFallbackException) and [DecoderFallbackException](xref:System.Text.DecoderFallbackException) classes do not meet your needs, derive a class from an exception object such as [Exception](xref:System.Exception) or [ArgumentException](xref:System.ArgumentException).</span></span>

### <a name="deriving-from-encoderfallback-or-decoderfallback"></a><span data-ttu-id="f9f27-316">Dérivation depuis EncoderFallback ou DecoderFallback</span><span class="sxs-lookup"><span data-stu-id="f9f27-316">Deriving from EncoderFallback or DecoderFallback</span></span>

<span data-ttu-id="f9f27-317">Pour implémenter une solution de stratégie de secours personnalisée, vous devez créer une classe qui hérite d’[EncoderFallback](xref:System.Text.EncoderFallback) pour les opérations d’encodage, et de [DecoderFallback](xref:System.Text.DecoderFallback) pour les opérations de décodage.</span><span class="sxs-lookup"><span data-stu-id="f9f27-317">To implement a custom fallback solution, you must create a class that inherits from [EncoderFallback](xref:System.Text.EncoderFallback) for encoding operations, and from [DecoderFallback](xref:System.Text.DecoderFallback) for decoding operations.</span></span> <span data-ttu-id="f9f27-318">Les instances de ces classes sont passées à la méthode [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) et servent d’intermédiaire entre la classe d’encodage et l’implémentation de la stratégie de secours.</span><span class="sxs-lookup"><span data-stu-id="f9f27-318">Instances of these classes are passed to the [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) method and serve as the intermediary between the encoding class and the fallback implementation.</span></span>

<span data-ttu-id="f9f27-319">Quand vous créez une solution de secours personnalisée pour un encodeur ou un décodeur, vous devez implémenter les membres suivants :</span><span class="sxs-lookup"><span data-stu-id="f9f27-319">When you create a custom fallback solution for an encoder or decoder, you must implement the following members:</span></span>

* <span data-ttu-id="f9f27-320">La propriété [EncoderFallback.MaxCharCount](xref:System.Text.EncoderFallback.MaxCharCount) ou [DecoderFallback.MaxCharCount](xref:System.Text.DecoderFallback.MaxCharCount), qui retourne le nombre maximal possible de caractères que les stratégies de secours la mieux adaptée, pour les remplacements ou pour les exceptions peuvent retourner pour remplacer un caractère unique.</span><span class="sxs-lookup"><span data-stu-id="f9f27-320">The [EncoderFallback.MaxCharCount](xref:System.Text.EncoderFallback.MaxCharCount) or [DecoderFallback.MaxCharCount](xref:System.Text.DecoderFallback.MaxCharCount) property, which returns the maximum possible number of characters that the best-fit, replacement, or exception fallback can return to replace a single character.</span></span> <span data-ttu-id="f9f27-321">Pour une stratégie de secours pour les exceptions personnalisée, sa valeur est zéro.</span><span class="sxs-lookup"><span data-stu-id="f9f27-321">For a custom exception fallback, its value is zero.</span></span> 

* <span data-ttu-id="f9f27-322">La méthode [EncoderFallback.CreateFallbackBuffer](xref:System.Text.EncoderFallback.CreateFallbackBuffer) ou [DecoderFallback.CreateFallbackBuffer](xref:System.Text.DecoderFallback.CreateFallbackBuffer) qui retourne votre implémentation [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) ou [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) personnalisée.</span><span class="sxs-lookup"><span data-stu-id="f9f27-322">The [EncoderFallback.CreateFallbackBuffer](xref:System.Text.EncoderFallback.CreateFallbackBuffer) or [DecoderFallback.CreateFallbackBuffer](xref:System.Text.DecoderFallback.CreateFallbackBuffer) method, which returns your custom [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) or [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) implementation.</span></span> <span data-ttu-id="f9f27-323">La méthode est appelée par l'encodeur quand il rencontre le premier caractère qu'il est impossible d'encoder correctement, ou par le décodeur quand il rencontre le premier octet qu'il est impossible de décoder correctement.</span><span class="sxs-lookup"><span data-stu-id="f9f27-323">The method is called by the encoder when it encounters the first character that it is unable to successfully encode, or by the decoder when it encounters the first byte that it is unable to successfully decode.</span></span>

### <a name="deriving-from-encoderfallbackbuffer-or-decoderfallbackbuffer"></a><span data-ttu-id="f9f27-324">Dérivation depuis EncoderFallbackBuffer ou DecoderFallbackBuffer</span><span class="sxs-lookup"><span data-stu-id="f9f27-324">Deriving from EncoderFallbackBuffer or DecoderFallbackBuffer</span></span>

<span data-ttu-id="f9f27-325">Pour implémenter une solution de stratégie de secours personnalisée, vous devez aussi créer une classe qui hérite d’[EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) pour les opérations d’encodage, et de [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) pour les opérations de décodage.</span><span class="sxs-lookup"><span data-stu-id="f9f27-325">To implement a custom fallback solution, you must also create a class that inherits from [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) for encoding operations, and from [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) for decoding operations.</span></span> <span data-ttu-id="f9f27-326">Les instances de ces classes sont retournées par la méthode `CreateFallbackBuffer` des classes [EncoderFallback](xref:System.Text.EncoderFallback) et [DecoderFallback](xref:System.Text.DecoderFallback).</span><span class="sxs-lookup"><span data-stu-id="f9f27-326">Instances of these classes are returned by the `CreateFallbackBuffer` method of the [EncoderFallback](xref:System.Text.EncoderFallback) and [DecoderFallback](xref:System.Text.DecoderFallback) classes.</span></span> <span data-ttu-id="f9f27-327">La méthode [EncoderFallback.CreateFallbackBuffer](xref:System.Text.EncoderFallback.CreateFallbackBuffer) est appelée par l’encodeur quand il rencontre le premier caractère qu’il ne peut pas encoder, et la méthode [DecoderFallback.CreateFallbackBuffer](xref:System.Text.DecoderFallback.CreateFallbackBuffer) est appelée par le décodeur quand il rencontre un ou plusieurs octets qu’il ne peut pas décoder.</span><span class="sxs-lookup"><span data-stu-id="f9f27-327">The [EncoderFallback.CreateFallbackBuffer](xref:System.Text.EncoderFallback.CreateFallbackBuffer) method is called by the encoder when it encounters the first character that it is not able to encode, and the [DecoderFallback.CreateFallbackBuffer](xref:System.Text.DecoderFallback.CreateFallbackBuffer) method is called by the decoder when it encounters one or more bytes that it is not able to decode.</span></span> <span data-ttu-id="f9f27-328">Les classes [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) et [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) fournissent l’implémentation de la stratégie de secours.</span><span class="sxs-lookup"><span data-stu-id="f9f27-328">The [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) and [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) classes provide the fallback implementation.</span></span> <span data-ttu-id="f9f27-329">Chaque instance représente une mémoire tampon qui contient les caractères de secours destinés à remplacer le caractère qui ne peut pas être encodé ou la séquence d'octets qui ne peut pas être décodée.</span><span class="sxs-lookup"><span data-stu-id="f9f27-329">Each instance represents a buffer that contains the fallback characters that will replace the character that cannot be encoded or the byte sequence that cannot be decoded.</span></span>

<span data-ttu-id="f9f27-330">Quand vous créez une solution de secours personnalisée pour un encodeur ou un décodeur, vous devez implémenter les membres suivants :</span><span class="sxs-lookup"><span data-stu-id="f9f27-330">When you create a custom fallback solution for an encoder or decoder, you must implement the following members:</span></span>

* <span data-ttu-id="f9f27-331">La méthode [EncoderFallbackBuffer.Fallback](xref:System.Text.EncoderFallbackBuffer.%23ctor) ou [DecoderFallbackBuffer.Fallback](xref:System.Text.DecoderFallbackBuffer.Fallback(System.Byte[],System.Int32)).</span><span class="sxs-lookup"><span data-stu-id="f9f27-331">The [EncoderFallbackBuffer.Fallback](xref:System.Text.EncoderFallbackBuffer.%23ctor) or [DecoderFallbackBuffer.Fallback](xref:System.Text.DecoderFallbackBuffer.Fallback(System.Byte[],System.Int32)) method.</span></span> <span data-ttu-id="f9f27-332">[EncoderFallbackBuffer.Fallback](xref:System.Text.EncoderFallbackBuffer.Fallback(System.Char,System.Char,System.Int32)) est appelée par l’encodeur pour fournir à la mémoire tampon de la stratégie de secours des informations concernant le caractère qu’elle ne peut pas encoder.</span><span class="sxs-lookup"><span data-stu-id="f9f27-332">[EncoderFallbackBuffer.Fallback](xref:System.Text.EncoderFallbackBuffer.Fallback(System.Char,System.Char,System.Int32)) is called by the encoder to provide the fallback buffer with information about the character that it cannot encode.</span></span> <span data-ttu-id="f9f27-333">Étant donné que le caractère à encoder peut être une paire de substitution, cette méthode est surchargée.</span><span class="sxs-lookup"><span data-stu-id="f9f27-333">Because the character to be encoded may be a surrogate pair, this method is overloaded.</span></span> <span data-ttu-id="f9f27-334">Le caractère à encoder et son index dans la chaîne sont passés à une surcharge.</span><span class="sxs-lookup"><span data-stu-id="f9f27-334">One overload is passed the character to be encoded and its index in the string.</span></span> <span data-ttu-id="f9f27-335">La demi-zone haute et la demi-zone basse, ainsi que son index dans la chaîne, sont passés à la deuxième surcharge.</span><span class="sxs-lookup"><span data-stu-id="f9f27-335">The second overload is passed the high and low surrogate along with its index in the string.</span></span> <span data-ttu-id="f9f27-336">La méthode [DecoderFallbackBuffer.Fallback](xref:System.Text.DecoderFallbackBuffer.Fallback(System.Byte[],System.Int32)) est appelée par le décodeur pour fournir à la mémoire tampon de la stratégie de secours des informations sur les octets qu’elle ne peut pas décoder.</span><span class="sxs-lookup"><span data-stu-id="f9f27-336">The [DecoderFallbackBuffer.Fallback](xref:System.Text.DecoderFallbackBuffer.Fallback(System.Byte[],System.Int32)) method is called by the decoder to provide the fallback buffer with information about the bytes that it cannot decode.</span></span> <span data-ttu-id="f9f27-337">Cette méthode reçoit un tableau d'octets qu'elle ne peut pas décoder, ainsi que l'index du premier octet.</span><span class="sxs-lookup"><span data-stu-id="f9f27-337">This method is passed an array of bytes that it cannot decode, along with the index of the first byte.</span></span> <span data-ttu-id="f9f27-338">La méthode de secours doit retourner `true` si la mémoire tampon de secours peut fournir un ou plusieurs caractères les mieux adaptés ou de remplacement ; sinon, elle doit retourner `false`.</span><span class="sxs-lookup"><span data-stu-id="f9f27-338">The fallback method should return `true` if the fallback buffer can supply a best-fit or replacement character or characters; otherwise, it should return `false`.</span></span> <span data-ttu-id="f9f27-339">Pour une stratégie de secours pour les exceptions, la méthode de secours doit lever une exception.</span><span class="sxs-lookup"><span data-stu-id="f9f27-339">For an exception fallback, the fallback method should throw an exception.</span></span>

* <span data-ttu-id="f9f27-340">La méthode [EncoderFallbackBuffer.GetNextChar](xref:System.Text.EncoderFallbackBuffer.GetNextChar) ou [DecoderFallbackBuffer.GetNextChar](xref:System.Text.DecoderFallbackBuffer.GetNextChar), qui est appelée à plusieurs reprises par l’encodeur ou le décodeur pour obtenir le caractère suivant de la mémoire tampon de la stratégie de secours.</span><span class="sxs-lookup"><span data-stu-id="f9f27-340">The [EncoderFallbackBuffer.GetNextChar](xref:System.Text.EncoderFallbackBuffer.GetNextChar) or [DecoderFallbackBuffer.GetNextChar](xref:System.Text.DecoderFallbackBuffer.GetNextChar) method, which is called repeatedly by the encoder or decoder to get the next character from the fallback buffer.</span></span> <span data-ttu-id="f9f27-341">Quand tous les caractères de secours ont été retournés, la méthode doit retourner U+0000.</span><span class="sxs-lookup"><span data-stu-id="f9f27-341">When all fallback characters have been returned, the method should return U+0000.</span></span> 

* <span data-ttu-id="f9f27-342">La propriété [EncoderFallbackBuffer.Remaining](xref:System.Text.EncoderFallbackBuffer.Remaining) ou [DecoderFallbackBuffer.Remaining](xref:System.Text.DecoderFallbackBuffer.Remaining), qui retourne le nombre de caractères restants dans la mémoire tampon de la stratégie de secours.</span><span class="sxs-lookup"><span data-stu-id="f9f27-342">The [EncoderFallbackBuffer.Remaining](xref:System.Text.EncoderFallbackBuffer.Remaining) or [DecoderFallbackBuffer.Remaining](xref:System.Text.DecoderFallbackBuffer.Remaining) property, which returns the number of characters remaining in the fallback buffer.</span></span>

* <span data-ttu-id="f9f27-343">La méthode [EncoderFallbackBuffer.MovePrevious](xref:System.Text.EncoderFallbackBuffer.MovePrevious) ou [DecoderFallbackBuffer.MovePrevious](xref:System.Text.DecoderFallbackBuffer.MovePrevious), qui déplace la position actuelle dans la mémoire tampon de la stratégie de secours vers le caractère précédent.</span><span class="sxs-lookup"><span data-stu-id="f9f27-343">The [EncoderFallbackBuffer.MovePrevious](xref:System.Text.EncoderFallbackBuffer.MovePrevious) or [DecoderFallbackBuffer.MovePrevious](xref:System.Text.DecoderFallbackBuffer.MovePrevious) method, which moves the current position in the fallback buffer to the previous character.</span></span>

* <span data-ttu-id="f9f27-344">La méthode [EncoderFallbackBuffer.Reset](xref:System.Text.EncoderFallbackBuffer.Reset) ou [DecoderFallbackBuffer.Reset](xref:System.Text.DecoderFallbackBuffer.Reset), qui réinitialise la mémoire tampon de la stratégie de secours.</span><span class="sxs-lookup"><span data-stu-id="f9f27-344">The [EncoderFallbackBuffer.Reset](xref:System.Text.EncoderFallbackBuffer.Reset) or [DecoderFallbackBuffer.Reset](xref:System.Text.DecoderFallbackBuffer.Reset) method, which reinitializes the fallback buffer.</span></span>

<span data-ttu-id="f9f27-345">Si l’implémentation de la stratégie de secours est une stratégie de secours la mieux adaptée ou pour les remplacements, les classes dérivées d’[EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) et [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) gèrent également deux champs d’instance privés : le nombre exact de caractères dans la mémoire tampon et l’index du caractère suivant dans la mémoire tampon à retourner.</span><span class="sxs-lookup"><span data-stu-id="f9f27-345">If the fallback implementation is a best-fit fallback or a replacement fallback, the classes derived from [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) and [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) also maintain two private instance fields: the exact number of characters in the buffer; and the index of the next character in the buffer to return.</span></span>

### <a name="an-encoderfallback-example"></a><span data-ttu-id="f9f27-346">Exemple basé sur EncoderFallback</span><span class="sxs-lookup"><span data-stu-id="f9f27-346">An EncoderFallback example</span></span>

<span data-ttu-id="f9f27-347">L’exemple précédent utilisait une stratégie de sauvegarde pour les remplacements pour remplacer les caractères Unicode qui ne correspondaient pas aux caractères ASCII par un astérisque (\*).</span><span class="sxs-lookup"><span data-stu-id="f9f27-347">An earlier example used replacement fallback to replace Unicode characters that did not correspond to ASCII characters with an asterisk (\*).</span></span> <span data-ttu-id="f9f27-348">L'exemple suivant utilise à la place une implémentation de stratégie de secours la mieux adaptée personnalisée pour fournir un meilleur mappage des caractères non-ASCII.</span><span class="sxs-lookup"><span data-stu-id="f9f27-348">The following example uses a custom best-fit fallback implementation instead to provide a better mapping of non-ASCII characters.</span></span>

<span data-ttu-id="f9f27-349">Le code suivant définit une classe nommée `CustomMapper` qui est dérivée d’[EncoderFallback](xref:System.Text.EncoderFallback) pour gérer le mappage le mieux adapté des caractères non-ASCII.</span><span class="sxs-lookup"><span data-stu-id="f9f27-349">The following code defines a class named `CustomMapper` that is derived from [EncoderFallback](xref:System.Text.EncoderFallback) to handle the best-fit mapping of non-ASCII characters.</span></span> <span data-ttu-id="f9f27-350">Sa méthode `CreateFallbackBuffer` renvoie un objet `CustomMapperFallbackBuffer`, qui fournit l’implémentation [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer).</span><span class="sxs-lookup"><span data-stu-id="f9f27-350">Its `CreateFallbackBuffer` method returns a `CustomMapperFallbackBuffer` object, which provides the [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) implementation.</span></span> <span data-ttu-id="f9f27-351">La classe `CustomMapper` utilise un objet [Dictionary&lt;TKey, TValue&gt;](xref:System.Collections.Generic.Dictionary%602) pour stocker les mappages des caractères Unicode non pris en charge (la valeur de la clé) et leurs caractères 8 bits correspondants (qui sont stockés dans deux octets consécutifs dans un entier 64 bits).</span><span class="sxs-lookup"><span data-stu-id="f9f27-351">The `CustomMapper` class uses a [Dictionary&lt;TKey, TValue&gt;](xref:System.Collections.Generic.Dictionary%602) object to store the mappings of unsupported Unicode characters (the key value) and their corresponding 8-bit characters (which are stored in two consecutive bytes in a 64-bit integer).</span></span> <span data-ttu-id="f9f27-352">Pour que ce mappage soit disponible pour la mémoire tampon de secours, l'instance de `CustomMapper` est passée comme paramètre au constructeur de classe `CustomMapperFallbackBuffer`.</span><span class="sxs-lookup"><span data-stu-id="f9f27-352">To make this mapping available to the fallback buffer, the `CustomMapper` instance is passed as a parameter to the `CustomMapperFallbackBuffer` class constructor.</span></span> <span data-ttu-id="f9f27-353">Comme le mappage le plus long est la chaîne "INF" pour le caractère Unicode U+221E, la propriété `MaxCharCount` retourne 3.</span><span class="sxs-lookup"><span data-stu-id="f9f27-353">Because the longest mapping is the string "INF" for the Unicode character U+221E, the `MaxCharCount` property returns 3.</span></span> 

```csharp
public class CustomMapper : EncoderFallback
{
   public string DefaultString;
   internal Dictionary<ushort, ulong> mapping;

   public CustomMapper() : this("*")
   {   
   }

   public CustomMapper(string defaultString)
   {
      this.DefaultString = defaultString;

      // Create table of mappings
      mapping = new Dictionary<ushort, ulong>();
      mapping.Add(0x24C8, 0x53);
      mapping.Add(0x2075, 0x35);
      mapping.Add(0x221E, 0x49004E0046);
   }

   public override EncoderFallbackBuffer CreateFallbackBuffer()
   {
      return new CustomMapperFallbackBuffer(this);
   }

   public override int MaxCharCount
   {
      get { return 3; }
   } 
}
```

```vb
Public Class CustomMapper : Inherits EncoderFallback
   Public DefaultString As String
   Friend mapping As Dictionary(Of UShort, ULong)

   Public Sub New()
      Me.New("?")
   End Sub

   Public Sub New(ByVal defaultString As String)
      Me.DefaultString = defaultString

      ' Create table of mappings
      mapping = New Dictionary(Of UShort, ULong)
      mapping.Add(&H24C8, &H53)
      mapping.Add(&H2075, &H35)
      mapping.Add(&H221E, &H49004E0046)
   End Sub

   Public Overrides Function CreateFallbackBuffer() As System.Text.EncoderFallbackBuffer
      Return New CustomMapperFallbackBuffer(Me)
   End Function

   Public Overrides ReadOnly Property MaxCharCount As Integer
      Get
         Return 3
      End Get
   End Property
End Class
```

<span data-ttu-id="f9f27-354">Le code suivant définit la classe `CustomMapperFallbackBuffer`, qui est dérivée d’[EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer).</span><span class="sxs-lookup"><span data-stu-id="f9f27-354">The following code defines the `CustomMapperFallbackBuffer` class, which is derived from [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer).</span></span> <span data-ttu-id="f9f27-355">Le dictionnaire qui contient les mappages les mieux adaptés et qui est défini dans l'instance de `CustomMapper` est disponible à partir de son constructeur de classe.</span><span class="sxs-lookup"><span data-stu-id="f9f27-355">The dictionary that contains best-fit mappings and that is defined in the `CustomMapper` instance is available from its class constructor.</span></span> <span data-ttu-id="f9f27-356">Sa méthode `Fallback` retourne `true` si un des caractères Unicode que l'encodeur ASCII ne peut pas encoder est défini dans le dictionnaire de mappage ; sinon, elle retourne `false`.</span><span class="sxs-lookup"><span data-stu-id="f9f27-356">Its `Fallback` method returns `true` if any of the Unicode characters that the ASCII encoder cannot encode are defined in the mapping dictionary; otherwise, it returns `false`.</span></span> <span data-ttu-id="f9f27-357">Pour chaque stratégie de secours, la variable privée `count` indique le nombre de caractères qui restent à retourner, et la variable privée `index` indique la position du caractère suivant à retourner dans la mémoire tampon de la chaîne, `charsToReturn`.</span><span class="sxs-lookup"><span data-stu-id="f9f27-357">For each fallback, the private `count` variable indicates the number of characters that remain to be returned, and the private `index` variable indicates the position in the string buffer, `charsToReturn`, of the next character to return.</span></span> 

```csharp
public class CustomMapperFallbackBuffer : EncoderFallbackBuffer
{
   int count = -1;                   // Number of characters to return
   int index = -1;                   // Index of character to return
   CustomMapper fb; 
   string charsToReturn; 

   public CustomMapperFallbackBuffer(CustomMapper fallback)
   {
      this.fb = fallback;
   }

   public override bool Fallback(char charUnknownHigh, char charUnknownLow, int index)
   {
      // Do not try to map surrogates to ASCII.
      return false;
   }

   public override bool Fallback(char charUnknown, int index)
   {
      // Return false if there are already characters to map.
      if (count >= 1) return false;

      // Determine number of characters to return.
      charsToReturn = String.Empty;

      ushort key = Convert.ToUInt16(charUnknown);
      if (fb.mapping.ContainsKey(key)) {
         byte[] bytes = BitConverter.GetBytes(fb.mapping[key]);
         int ctr = 0;
         foreach (var byt in bytes) {
            if (byt > 0) {
               ctr++;
               charsToReturn += (char) byt;
            }
         }
         count = ctr;
      }
      else {
         // Return default.
         charsToReturn = fb.DefaultString;
         count = 1;
      }
      this.index = charsToReturn.Length - 1;

      return true;
   }

   public override char GetNextChar()
   {
      // We'll return a character if possible, so subtract from the count of chars to return.
      count--;
      // If count is less than zero, we've returned all characters.
      if (count < 0) 
         return '\u0000';

      this.index--;
      return charsToReturn[this.index + 1];
   }

   public override bool MovePrevious()
   {
      // Original: if count >= -1 and pos >= 0
      if (count >= -1) {
         count++;
         return true;
      }
      else {
         return false;
      }
   }

   public override int Remaining 
   {
      get { return count < 0 ? 0 : count; }
   }

   public override void Reset()
   {
      count = -1;
      index = -1;
   }
}
```

```vb
Public Class CustomMapperFallbackBuffer : Inherits EncoderFallbackBuffer

   Dim count As Integer = -1        ' Number of characters to return
   Dim index As Integer = -1        ' Index of character to return
   Dim fb As CustomMapper
   Dim charsToReturn As String

   Public Sub New(ByVal fallback As CustomMapper)
      MyBase.New()
      Me.fb = fallback
   End Sub

   Public Overloads Overrides Function Fallback(ByVal charUnknownHigh As Char, ByVal charUnknownLow As Char, ByVal index As Integer) As Boolean
      ' Do not try to map surrogates to ASCII.
      Return False
   End Function

   Public Overloads Overrides Function Fallback(ByVal charUnknown As Char, ByVal index As Integer) As Boolean
      ' Return false if there are already characters to map.
      If count >= 1 Then Return False

      ' Determine number of characters to return.
      charsToReturn = String.Empty

      Dim key As UShort = Convert.ToUInt16(charUnknown)
      If fb.mapping.ContainsKey(key) Then
         Dim bytes() As Byte = BitConverter.GetBytes(fb.mapping.Item(key))
         Dim ctr As Integer
         For Each byt In bytes
            If byt > 0 Then
               ctr += 1
               charsToReturn += Chr(byt)
            End If
         Next
         count = ctr
      Else
         ' Return default.
         charsToReturn = fb.DefaultString
         count = 1
      End If
      Me.index = charsToReturn.Length - 1

      Return True
   End Function

   Public Overrides Function GetNextChar() As Char
      ' We'll return a character if possible, so subtract from the count of chars to return.
      count -= 1
      ' If count is less than zero, we've returned all characters.
      If count < 0 Then Return ChrW(0)

      Me.index -= 1
      Return charsToReturn(Me.index + 1)
   End Function

   Public Overrides Function MovePrevious() As Boolean
      ' Original: if count >= -1 and pos >= 0
      If count >= -1 Then
         count += 1
         Return True
      Else
         Return False
      End If
   End Function

   Public Overrides ReadOnly Property Remaining As Integer
      Get
         Return If(count < 0, 0, count)
      End Get
   End Property

   Public Overrides Sub Reset()
      count = -1
      index = -1
   End Sub
End Class
```

<span data-ttu-id="f9f27-358">Le code suivant instancie ensuite l’objet `CustomMapper` et passe une instance de celui-ci à la méthode [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)).</span><span class="sxs-lookup"><span data-stu-id="f9f27-358">The following code then instantiates the `CustomMapper` object and passes an instance of it to the [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) method.</span></span> <span data-ttu-id="f9f27-359">La sortie indique que l'implémentation de la stratégie de secours la mieux adaptée gère correctement les trois caractères non-ASCII de la chaîne d'origine.</span><span class="sxs-lookup"><span data-stu-id="f9f27-359">The output indicates that the best-fit fallback implementation successfully handles the three non-ASCII characters in the original string.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Text;

class Program
{
   static void Main()
   {
      Encoding enc = Encoding.GetEncoding("us-ascii", new CustomMapper(), new DecoderExceptionFallback());

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      for (int ctr = 0; ctr <= str1.Length - 1; ctr++) {
         Console.Write("{0} ", Convert.ToUInt16(str1[ctr]).ToString("X4"));
         if (ctr == str1.Length - 1) 
            Console.WriteLine();
      }
      Console.WriteLine();

      // Encode the original string using the ASCII encoder.
      byte[] bytes = enc.GetBytes(str1);
      Console.Write("Encoded bytes: ");
      foreach (var byt in bytes)
         Console.Write("{0:X2} ", byt);

      Console.WriteLine("\n");

      // Decode the ASCII bytes.
      string str2 = enc.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      }
   }
}
```

```vb
Imports System.Text
Imports System.Collections.Generic

Module Module1

   Sub Main()
      Dim enc As Encoding = Encoding.GetEncoding("us-ascii", New CustomMapper(), New DecoderExceptionFallback())

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&H24C8), ChrW(&H2075), ChrW(&H221E))
      Console.WriteLine(str1)
      For ctr As Integer = 0 To str1.Length - 1
         Console.Write("{0} ", Convert.ToUInt16(str1(ctr)).ToString("X4"))
         If ctr = str1.Length - 1 Then Console.WriteLine()
      Next
      Console.WriteLine()

      ' Encode the original string using the ASCII encoder.
      Dim bytes() As Byte = enc.GetBytes(str1)
      Console.Write("Encoded bytes: ")
      For Each byt In bytes
         Console.Write("{0:X2} ", byt)
      Next
      Console.WriteLine()
      Console.WriteLine()

      ' Decode the ASCII bytes.
      Dim str2 As String = enc.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
         Console.WriteLine()
      End If
   End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="f9f27-360">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9f27-360">See also</span></span>

[<span data-ttu-id="f9f27-361">System.Text.Encoder</span><span class="sxs-lookup"><span data-stu-id="f9f27-361">System.Text.Encoder</span></span>](xref:System.Text.Encoder)

[<span data-ttu-id="f9f27-362">System.Text.EncoderFallback</span><span class="sxs-lookup"><span data-stu-id="f9f27-362">System.Text.EncoderFallback</span></span>](xref:System.Text.EncoderFallback)

[<span data-ttu-id="f9f27-363">System.Text.Decoder</span><span class="sxs-lookup"><span data-stu-id="f9f27-363">System.Text.Decoder</span></span>](xref:System.Text.Decoder)

[<span data-ttu-id="f9f27-364">System.Text.DecoderFallback</span><span class="sxs-lookup"><span data-stu-id="f9f27-364">System.Text.DecoderFallback</span></span>](xref:System.Text.DecoderFallback)

[<span data-ttu-id="f9f27-365">System.Text.Encoding</span><span class="sxs-lookup"><span data-stu-id="f9f27-365">System.Text.Encoding</span></span>](xref:System.Text.Encoding)





