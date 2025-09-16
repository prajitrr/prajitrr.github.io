---
title: "Home"
layout: default
sitemap: false
permalink: /
---

<style>
.jumbotron{
    padding:3%;
    padding-bottom:10px;
    padding-top:10px;
    margin-top:10px;
    margin-bottom:30px;
}

.headshot-wrapper {
  position: relative;
  display: inline-block;
  float: right;
  margin-left: 20px;
  perspective: 1000px;
  width: 350px;
  min-width: 30%;
  max-width: 100%;
  z-index: 10;
}

.headshot-img {
  display: block;
  width: 100%;
  border-radius: 16px;
  box-shadow: 0 4px 16px rgba(0,0,0,0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.headshot-wrapper:hover .headshot-img {
  box-shadow: 0 8px 30px rgba(106,130,251,0.5);
}

/* Spotify iframe wrapper */
.spotify-wrapper {
  position: relative;
  display: inline-block;
  float: right;
  clear: right;
  /* margin-left: 20px;
  margin-top: 20px;
  margin-bottom: 30px;
  perspective: 1000px;
  width: 350px;
  min-width: 30%;
  max-width: 100%; */
  z-index: 10;
  aspect-ratio: 1/1;
}

.spotify-iframe {
  display: block;
  width: 100%;
  height: 100%;
  border-radius: 16px;
  box-shadow: 0 4px 16px rgba(0,0,0,0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.spotify-wrapper:hover .spotify-iframe {
  box-shadow: 0 8px 30px rgba(106,130,251,0.5);
}
</style>


<div id="homeid" class="col-sm-12 col-xs-12">
<div class="headshot-wrapper">
  <img id="headshot-img" class="headshot-img" src="{{site.url}}{{site.baseurl}}/images/headshot.jpg" alt="Headshot">
</div>




<script>
// 3D tilt effect on mouse move
document.addEventListener('DOMContentLoaded', function() {
  // Headshot tilt effect
  const img = document.getElementById('headshot-img');
  const wrapper = document.querySelector('.headshot-wrapper');
  
  if (img && wrapper) {
    wrapper.addEventListener('mousemove', function(e) {
      const rect = wrapper.getBoundingClientRect();
      const x = e.clientX - rect.left;
      const y = e.clientY - rect.top;
      
      // Calculate center point
      const centerX = rect.width / 2;
      const centerY = rect.height / 2;
      
      // Calculate normalized position from center (-1 to 1)
      const xPercent = (x - centerX) / centerX;
      const yPercent = (y - centerY) / centerY;
      
      // Calculate distance from center (0 to 1)
      const distance = Math.min(1, Math.sqrt(xPercent*xPercent + yPercent*yPercent));
      
      // Apply tilt based on mouse position - inverse Y for natural feel
      // Max tilt of 8 degrees for subtle effect
      const tiltY = xPercent * 8 * distance;
      const tiltX = -yPercent * 8 * distance;
      
      // Apply transform - scaled based on distance from center
      const scale = 1 - (distance * 0.02); // Very slight scaling
      img.style.transform = `perspective(1000px) rotateX(${tiltX}deg) rotateY(${tiltY}deg) scale(${scale})`;
    });
    
    wrapper.addEventListener('mouseleave', function() {
      // Reset transform on mouse leave
      img.style.transform = 'perspective(1000px) rotateX(0) rotateY(0) scale(1)';
    });
  }
  
  // Spotify iframe tilt effect
  const spotifyWrapper = document.querySelector('.spotify-wrapper');
  const spotifyIframe = document.querySelector('.spotify-iframe');
  
  if (spotifyWrapper && spotifyIframe) {
    spotifyWrapper.addEventListener('mousemove', function(e) {
      const rect = spotifyWrapper.getBoundingClientRect();
      const x = e.clientX - rect.left;
      const y = e.clientY - rect.top;
      
      // Calculate center point
      const centerX = rect.width / 2;
      const centerY = rect.height / 2;
      
      // Calculate normalized position from center (-1 to 1)
      const xPercent = (x - centerX) / centerX;
      const yPercent = (y - centerY) / centerY;
      
      // Calculate distance from center (0 to 1)
      const distance = Math.min(1, Math.sqrt(xPercent*xPercent + yPercent*yPercent));
      
      // Apply tilt based on mouse position - inverse Y for natural feel
      // Max tilt of 6 degrees for subtle effect
      const tiltY = xPercent * 6 * distance;
      const tiltX = -yPercent * 6 * distance;
      
      // Apply transform
      spotifyIframe.style.transform = `perspective(1000px) rotateX(${tiltX}deg) rotateY(${tiltY}deg)`;
    });
    
    spotifyWrapper.addEventListener('mouseleave', function() {
      // Reset transform on mouse leave
      spotifyIframe.style.transform = 'perspective(1000px) rotateX(0) rotateY(0)';
    });
  }
});
</script>


<script>
//  // Spotify API Script

//  const spotifyWidget = document.createElement('iframe');
//  const clientID = "NONE";
//  const clientSecret = "NONE";

//  async function getSpotifyToken(clientId, clientSecret) {
//     const response = await fetch('https://accounts.spotify.com/api/token', {
//       method: 'POST',
//       headers: {
//         'Content-Type': 'application/x-www-form-urlencoded'
//       },
//       body: `grant_type=client_credentials&client_id=${clientId}&client_secret=${clientSecret}`
//     });
    
//     const data = await response.json();
//     return data.access_token;
//   }

// const token = await getSpotifyToken(clientID, clientSecret);

// async function fetchLastSong(){
//   const response = await fetch('https://api.spotify.com/v1/me/player/recently-played?limit=1', {
//     headers: {
//       'Authorization': `Bearer ${token}`
//     }
//   });
//   const data = await response.json();
  
//   // Embed song as iframe
//   const track = data.items[0].track;
//   const trackId = track.id;
//   return `https://open.spotify.com/embed/track/${trackId}?utm_source=generator&theme=0`;
// }

// const lastSongUrl = await fetchLastSong();

// async function fetchWebApi(endpoint, method, body) {
//   const res = await fetch(`https://api.spotify.com/${endpoint}`, {
//     headers: {
//       Authorization: `Bearer ${token}`,
//     },
//     method,
//     body:JSON.stringify(body)
//   });
//   return await res.json();
// }

// async function getTopTracks(){
//   // Endpoint reference : https://developer.spotify.com/documentation/web-api/reference/get-users-top-artists-and-tracks
//   return (await fetchWebApi(
//     'v1/me/top/tracks?time_range=long_term&limit=5', 'GET'
//   )).items;
// }

// const topTracks = await getTopTracks();
// console.log(
//   topTracks?.map(
//     ({name, artists}) =>
//       `${name} by ${artists.map(artist => artist.name).join(', ')}`
//   )
// );
</script>



<!-- <div class="spotify-wrapper">
<iframe
  class="spotify-iframe"
  title="Spotify Embed: Recommendation Playlist"
  src="{lastSongUrl}"
  width="100%"
  height="100%"
  frameborder="0"
  allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture"
  loading="lazy"
  style="width:350px; height:365px; margin-top:20px; margin-left:0px; margin-bottom:0px;">
</iframe>
</div> -->




<div style="text-align:justify">
### about me
Hi! Thank you for checking out my website! I'm Prajit Rajkumar, a second-year undergraduate student at [UC San Diego](https://ucsd.edu/) in [Thurgood Marshall College](https://marshall.ucsd.edu/). 

I'm pursuing a double major in [Biology with a Specialization in Bioinformatics](https://biology.ucsd.edu/education/undergrad/major-minor-programs/majors/requirements/bioinformatics/index.html) and [Mathematics-Computer Science](https://math.ucsd.edu/students/undergraduate/ma30-math-computer-science-b-s). 

Outside of class, I'm heavily involved with research as part of the [Dorrestein Lab](https://dorresteinlab.ucsd.edu/) at UCSD's [Skaggs School of Pharmacy & Pharmaceutical Sciences](https://pharmacy.ucsd.edu/), where I mainly focus on computational metabolomics. 

I'm also passionate about teaching and giving back to the academic community that has shaped me, which has led me to work as a [Supplemental Instruction Leader](https://aah.ucsd.edu/supplemental-instruction/index.html) for various mathematics courses as well as join UCSD's [Undergraduate Bioinformatics Club](https://ubicucsd.github.io/) as a board member and incoming vice president. 

In my free time, I like playing chess, long distance running, and watching anime.
</div>


<!-- <div class="jumbotron">
### Selected Publications
{% bibliography -f articles -q @*[selected=True]  %}
</div> -->