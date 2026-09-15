Rules and guidelines derived from the [DFKI-SLT/few-nerd](https://huggingface.co/datasets/DFKI-SLT/few-nerd/blob/main/README.md) dataset, with data samples 1–50 designated as "Round 1" and samples 51–100 as "Round 2."

Date: 2026-09-07

**Annotation Definitions:**
Named entities found within sentences are annotated using the following categories:

`person`
Proper nouns referring to specific individuals or real (non-fictional) figures.

`location`
Proper nouns referring to places, countries, regions, or provinces.

`event`
Proper nouns referring to events such as battles, famous demonstrations, or sports leagues.

`building`
Proper nouns referring to specific structures, such as skyscrapers, theaters, or government buildings.

`organization`
Proper nouns referring to groups of individuals united under a common banner or identity—including organizations, companies, teams, families, political parties, and political movements.

`product`
Proper nouns referring to tangible, man-made products, such as games, devices, tools, or engines.

`art`
Proper nouns referring to intangible, man-made products with an artistic nature, such as the titles of songs, films, and plays, or the names of fictional characters.

`other`
Proper nouns that do not fall into any of the previous categories—such as animals, university degrees, famous experiments (do not annotate unless the sentence explains the abbreviation or meaning of the name), or chemical compounds.

## Annotation Instructions:
1. Pay close attention to the nature of named entities; generic nouns (common nouns) are not to be annotated. Example: The word "office" is not considered a "building" because it is a generic noun, not a proper noun identifying a specific office.
Grill Room = building
Room = No entry
Errors frequently occur with names that appear to be proper nouns but are not—especially regarding products.

2. Determining the scope of the annotation: If a proper noun cannot be understood without the word preceding it, that word is included in the annotation (e.g., "Grill Room," where "grill" is not understood without "room"). Conversely, if it is understood without the additional word, that word is excluded from the description (e.g., "B-52 pilot," where "B-52" is understood as a product without adding the word "product").
The primary goal is to enhance the AI's comprehension of the information—ensuring, for instance, that it does not mistake the product name literally for "B-52 pilot," or mistakenly interpret "grill" as a building located inside a "room."

3. Human Error
Errors are inevitable; therefore, it is advisable to work in intervals and review one's own work (QA) at the end of each batch before submission to minimize errors and maximize accuracy. Periodic review of the guidelines is also recommended.
Human error may manifest as a failure to grasp the sentence context, rushing through data annotation (leading to errors in the description itself or in typing), overlooking names that require annotation, or forgetting annotation conventions over time and relying instead on personal impressions.

## Edge Cases
1. Organization vs. Building
When a building is annotated in a way that makes it a distinct entity (a proper noun in its own right), it is annotated as a "building."
If it is annotated as a specific collective group, it is annotated as an "organization."
Example:
high school = building
high school of California = organization

2. Building vs. location
Some structures are considered sites or famous areas rather than specific buildings—such as parks—because the emphasis is not on their construction materials.

3. Words with multiple potential interpretations
Here, understanding the sentence context is crucial; AI interprets the intended meaning based on the surrounding words. For example, "England" could refer to the sports team (annotated as *organization*) or the country itself (annotated as *location*).

4. Product vs. Arts
The distinction focuses on whether a product is tangible or intangible. Both are human-made, but the difference lies in the artistic nature and physical tangibility of the item.
Regarding video games: if the reference is to gaming consoles, they are classified as *product*; if the reference is to the game software itself, it is classified as *arts*.

5. Person vs. Arts
Fictional or non-real characters are annotated as *arts* rather than *person*, as they are human creations rather than tangible entities.

## Some previous errors:
1. The word "protein" should not be annotated as *other*; it is a common noun rather than a proper noun, as no specific type of protein is annotated.
2. Television programs should be annotated as *organization*, not *other*.
3. Categorizing projects as *product*.
4. Categorizing churches as *organization*; the correct annotation is *building*.