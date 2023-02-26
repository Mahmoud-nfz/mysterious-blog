<div id="Home" class=" h-[100vh] p-5" style="background-color: rgb(43, 41, 41);">
    <h1 class="text-5xl mb-3">Hello there curious wanderer</h1>
    <h1 class="text-5xl font-bold">All beginnings are important, so here's yours!</h1>
    <br>
    
    <div class="mb-3">
          <h1 id="tittle" class="text-3xl font-bold leading-normal">
            {@html title.slice(0, titleIndex)}
          </h1>
    </div>
    {#if !hidden}
    <p>0x690B9A9E9aa1C9dB991C7721a92d351Db4FaC990</p>
    <a href="https://gentleman-restaurant.onrender.com">
      <img width="200px" height="200px" alt="0x690B9A9E9aa1C9dB991C7721a92d351Db4FaC990" src="{testImage}"/>
    </a>
    {/if}
</div>


<script>
  import { onMount } from 'svelte';
  import testImage from '../assets/test.png';

  import Cookies from 'js-cookie';
  
  let title = `<aa>C</aa>redible sources are essential in investigative journalism.<br/>
        <aa>O</aa>btaining information from trustworthy individuals is crucial to the accuracy of the story.<br/>
        <aa>O</aa>mitting important details can undermine the credibility of the investigation.<br/>
        <aa>K</aa>eeping meticulous notes is key when conducting interviews. <br/>
        <aa>I</aa>nvestigative journalists must be persistent in their pursuit of the truth.<br/>
        <aa>E</aa>agle-eyed journalists pursue every lead in their investigation for the truth.
     `;

  let titleIndex = 0;

  ////
  let i = 0;
  
  
  let hidden = true;
  setInterval(() => {
        console.log("fytjtfh");
      if (Cookies.get('beginning') == 'true') {
        hidden = false;
      }
  }, 1000);
  ////

  function handleTypingFinished() {
    const event = new CustomEvent('first-typing-finished', {
      detail: {}
    });
    dispatchEvent(event);
  }

  function typeTitle() {
    setTimeout(() => {
      if(title[titleIndex+1] == '<'){
        titleIndex += 3 ;
      }
      else{
        titleIndex++;
      }
      if (titleIndex <= title.length) {
        typeTitle();
      }
      else{
        handleTypingFinished();
      }
    }, 30);
  }

  onMount(() => {

    Cookies.set('beginning', 'false')
    // document.cookie = `view_hidden=false;max-age=604800;domain=localhost`;
    typeTitle();
  });
</script>

