<script>
  import { goto } from '$app/navigation';
  
  import Image from "../atoms/Image.svelte";
  import Margin from "../atoms/Margin.svelte";
  import Text from "../atoms/Text.svelte";
  import Button from "../atoms/Button.svelte";
  import ClickableImage from "../molecules/ClickableImage.svelte";

  import MockupInMyTemple from "../../assets/img/mockups/inmytemple_mockup_desktop2.jpg"
  import MockupCombiBassin from "../../assets/img/mockups/combibassin_mockup_desktop1.jpg"
  import MockupHavrePaix from "../../assets/img/mockups/havrepaix_mockup_mobile.jpg"
</script>
 
<div class='main-projects'>
  <Margin marginBottom="var(--spacing-1)">
    <Text
      textTag='h2'
      class='text-preset-2'
    >
      Mes projets
    </Text>
  </Margin>

  <div class="main-projects__mosaic">
    <ClickableImage linkUrl="/projets/in-my-temple">
      <Image
        imageSrc={MockupInMyTemple}
        imageAlt="Mockup du site web In my temple développé par Chloé Doustalet"
        imageWidth=100%
        imageHeight=663
        slot="image"
      />
      <span slot="title"> In my temple </span>
    </ClickableImage>

    <ClickableImage linkUrl="/projets/havre-de-paix">
      <Image
        imageSrc={MockupHavrePaix}
        imageAlt="Mockup du site internet Havre de paix développé par Chloé Doustalet"
        imageWidth=50%
        imageHeight=298
        slot="image"
      />
      <span slot="title"> Havre de paix </span>
    </ClickableImage>

    <ClickableImage linkUrl="/projets/combi-du-bassin">
      <Image
        imageSrc={MockupCombiBassin}
        imageAlt="Mockup du site web Les combis du bassin développé par Chloé Doustalet"
        imageWidth=100%
        imageHeight=344
        slot="image"
      />
      <span slot="title"> Les combis du bassin </span>
    </ClickableImage>
  </div>

  <Margin marginTop="40px">
    <Button class="block-center" on:click={() => goto('/projets')}> Découvrir d'autres projets </Button>
  </Margin>
  
</div>

<style>
  .main-projects{
    padding: var(--spacing-3) var(--spacing-4);
    background-color: var(--color-background-secondary);
  }

  .main-projects__mosaic{
    display: grid;
    grid-template-columns: repeat(4, 25%);
    grid-template-rows: 50% 50%;
    column-gap: var(--spacing-1);
  }

  :global(.main-projects__mosaic .clickable-image:first-child){
    grid-column: 1 / 3;
    grid-row: 1 / 3;  
  }

  :global(.main-projects__mosaic .clickable-image:nth-child(2)){
    grid-column: 3 / 5;
    grid-row: 1 / 2;  
  }

  :global(.main-projects__mosaic .clickable-image:nth-child(2) img){
    object-position: center -120px;  
  }

  :global(.main-projects__mosaic .clickable-image:last-child){
    grid-column: 3 / 5;
    grid-row: 2 / 3;  
  }

  @media screen and (max-width: 1100px) {
    .main-projects{
      padding: var(--spacing-4) var(--spacing-5);
    }

    .main-projects__mosaic{
      width: calc(100% - 60px);
      column-gap: 10px;
      row-gap: 10px;
    }
  }

  @media screen and (max-width: 600px) {
    .main-projects__mosaic{
      width: 100%;
      display: flex;
      flex-wrap: wrap;
      row-gap: var(--spacing-1);
    }

    :global(.main-projects__mosaic .clickable-image){
      width: 100%;
      height: 250px;
    } 

    :global(.main-projects__mosaic .clickable-image img){
      width: 100%;
      height: 250px;
    } 
  }
</style>