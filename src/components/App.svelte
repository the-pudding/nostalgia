<script>
  import { getContext } from "svelte";
  import { onMount } from 'svelte';
  import Demo from "$components/demo/Demo.svelte";
  import WIP from "$components/helpers/WIP.svelte";
  
  // import swiper modules
  import { Swiper, SwiperSlide } from 'swiper/svelte';
  import { Pagination } from "swiper";
  
  // import swiper styles
  import 'swiper/css';
  import "swiper/css/pagination";

  // import Footer from "$components/Footer.svelte";
  let body;
  let html;
  let pageW;
  let pageH;
  let pageRatio;
  let pageOrientation;

  onMount(() => {
    body = document.body;
    html = document.documentElement;

    pageW = Math.max( body.scrollWidth, body.offsetWidth, 
                html.clientWidth, html.scrollWidth, html.offsetWidth );
    pageH = Math.max( body.scrollHeight, body.offsetHeight, 
                html.clientHeight, html.scrollHeight, html.offsetHeight );
    pageRatio = pageW/pageH

    pageOrientation = (pageRatio >= 1) ? "horizontal" : "vertical"
    console.log(pageOrientation)
  });
        
  

  const copy = getContext("copy");
</script>

<Swiper
    spaceBetween={50}
    slidesPerView={1}
    direction={pageOrientation}
    pagination={{ 
      dynamicBullets: true, 
      clickable: true }}
    modules={[Pagination]}
    on:slideChange={() => console.log('slide change')}
    on:swiper={(e) => console.log(e.detail[0])}
  >
    <SwiperSlide>Slide 1</SwiperSlide>
    <SwiperSlide>Slide 2</SwiperSlide>
    <SwiperSlide>Slide 3</SwiperSlide>
    <SwiperSlide>Slide 4</SwiperSlide>
    ...
</Swiper>

<!-- <WIP />
<Demo /> -->
<!-- <Footer /> -->
