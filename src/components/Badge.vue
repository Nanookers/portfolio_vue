<template>
    <div class="card">
        <div class="profileImage">
            <img src="../assets/profilePix.jpeg"/>
        </div>
        <div class="infoSide">
            <div class="titles">
                <h1>Connor Clark</h1>
                    <h3>Full Stack Developer | Aspring Dungeon Master</h3>
                    <p>A full stack developer who doesn't rely on lucky skill checks. Lorem Ipsum this bullshit!</p>
            </div>
            <div class="externalLinks">
                <a href="https://www.linkedin.com/in/connor-clark-7bb39919b/" target="_blank" 
                    title="https://www.linkedin.com/in/connor-clark-7bb39919b/">
                    <i style='font-size:30px' class='fab' id="linkedIn">&#xf0e1;</i>
                </a>
                
                <i v-on:click="say('connordeclark@gmail.com')" style='font-size:32px' 
                    class='material-icons' id="email" title="connordeclark@gmail.com">&#xe0be;</i>

                <a href="https://github.com/Nanookers" target="_blank" title="https://github.com/Nanookers">
                    <i style='font-size:30px' class='fab' id="gitHub">&#xf092;</i>
                </a>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
  export default {
    methods: {
    // Following function is used to copy my email to a clipboard. 
      say: async function (address: string) {
        console.log(address)
        try{
            await navigator.clipboard.writeText(address)
            alert('Copied Email')
        } catch{
            alert('Cannot Copy')
        }
      },
    },
  };

</script>

<style scoped>
.card {
    display: flex;
    max-width: 650px; /* Use max-width instead of width */
    padding: 7px;
}

/* Use flex-wrap to wrap the links when there's not enough space */
.externalLinks {
    display: flex;
    justify-content: flex-end; /* Change 'end' to 'flex-end' for better browser support */
    transform: translateY(65%);
}

.fab,
.material-icons {
    cursor: pointer;
    margin-right: 12px;
}

.profileImage {
    border-radius: 50%;
    overflow: hidden;
    width: 175px;
    height: 175px;
}

.profileImage img {
    width: 100%;
    height: 100%;
}

.titles {
    margin-left: 1rem;
    width: 100%; /* Remove the fixed width to allow responsive adjustments */
    max-width: 450px; /* Use max-width instead of width */
    padding-bottom: 5px;
}

.titles h1 {
    margin-bottom: 10px;
    margin-top: 10px;
}

.titles h3 {
    margin: 0;
    padding: 0;
}

.titles p {
    margin: 0;
    padding-top: 8px;
    width: 100%;
    max-width: 392px;
}

svg {
    width: 100px;
    height: 100px;
}

/* Add a media query for smaller screens */
@media (max-width: 768px) {
    .card {
        flex-direction: column; /* Stack the content in a column */
        align-items: center; /* Center the items in the card */
    }
    .externalLinks {
        justify-content: center; /* Center the links in smaller screens */
        transform: none; /* Remove the translateY */
    }
}
</style>
