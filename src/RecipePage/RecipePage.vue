<script setup lang="ts">




export type TRecipe = {
    picture: {
        src: string,
        alt: string,
    },
    title: string,
    description: string,
    preparationTime: {
        total: string,
        preparation: string,
        cooking: string
    },
    ingredients: string[],
    instructions: Array<{ title: string, text: string }>,
    nutrition: {
        description: string,
        table: Array<
            {
                title: string,
                value: string
            }
        >
    }
}

defineProps<TRecipe>()

</script>

<template>
    <section class="recipe">
    
        <div class="recipeImageContainer"><img v-bind:src="picture.src" v-bind:alt="picture.alt" class="recipeImage" /></div>

        <section class="recipeHeader">
            <h1 class="recipeHeader_title titleSerif">{{ title }}</h1>
            <p class="recipeHeader_description">{{ description }}</p>
        </section>

        <section class="preparationTime recipeInfoBox ">
            <h3 class="preparationTime_title recipeInfoBox_title">Preparation time</h3>
            <ul class="preparationTime_list recipeInfoBox_list recipeInfoBox_list_ul">
                <li class="preparationTime_listItem recipeInfoBox_listItem"><span class="recipeInfoBox_listItem_text"><span
                        class="preparationTime_subtitle recipeInfoBox_subtitle">Total:</span><span
                        class="preparationTime_text">{{ preparationTime.total }}</span>
                    </span></li>
                <li class="preparationTime_listItem recipeInfoBox_listItem"><span class="recipeInfoBox_listItem_text">
                    <span
                            class="preparationTime_subtitle recipeInfoBox_subtitle">Preparation:</span><span
                            class="preparationTime_text">{{ preparationTime.preparation }}</span>
                </span></li>
                <li class="preparationTime_listItem recipeInfoBox_listItem"><span class="recipeInfoBox_listItem_text">
                    <span
                            class="preparationTime_subtitle recipeInfoBox_subtitle">Cooking:</span><span
                            class="preparationTime_text">{{ preparationTime.cooking }}</span>
                </span></li>
            </ul>
        </section>

        <section class="ingredients recipeSection">
            <h2 class="recipeSectionTitle titleSerif">Ingredients</h2>
            <ul class="ingredients_list recipeSection_list recipeSection_list_ul">
                <!-- {{ingredients.map(i=><li>{{i}}</li>}} -->
                <li class="ingredients_listItem recipeSection_listItem recipeSection_list_ul_Item" v-for="ingredient in ingredients">{{ ingredient
                    }}
                </li>
            </ul>
        </section>

        <section class="instructions recipeSection">
            <h2 class="recipeSectionTitle titleSerif">Instructions</h2>
            <ol class="instructions_list recipeSection_list recipeSection_list_ol">
                <li class="instructions_listItem recipeSection_listItem recipeSection_list_ol_Item" v-for="instruction in instructions"><span><span
                        class="instructionTitle recipeSection_list_Item__subTitle">{{ instruction.title }}</span><span class="instructionText">{{
                        instruction.text }}</span></span></li>
            </ol>
        </section>

        <section class="nutrition recipeSection">
            <h2 class="recipeSectionTitle titleSerif">Nutrition</h2>
            <div class="recipeSection_description">{{ nutrition.description }}</div>
            <table class="sectionTable">
                <tr class="sectionTable_row" v-for="row in nutrition.table">
                    <td class="sectionTable_data">{{ row.title }}</td>
                    <td class="sectionTable_data">{{ row.value }}</td>
                </tr>
            </table>
        </section>
    </section>
</template>

<style scoped src="./RecipePage.css">

</style>
