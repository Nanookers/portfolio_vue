<script lang="ts">
  export default {
    methods: {
      say: function (address: string) {
        console.log(address)
        // Next step is to figure out how to copy to clip board
      },
    },
  };

</script>
<template>
    <div class="card">
        <div class="profileImage">
            <img src="../assets/profilePix.jpeg"/>
        </div>
        <div class="infoSide">
            <div class="titles">
                <h1>Connor Clark</h1>
                    <h3>Full Stack Developer | Aspring Dungeon Master</h3>
                    <p>A full stack developer who doesn't rely on lucky skill checks. Lorem Ipsum List this</p>
            </div>
            <div class="externalLinks">
                <a href="https://www.linkedin.com/in/connor-clark-7bb39919b/" target="_blank">
                    <i style='font-size:30px' class='fab' id="linkedIn">&#xf0e1;</i>
                </a>
                
                <i v-on:click="say('connordeclark@gmail.com')" style='font-size:32px' class='material-icons' id="email">&#xe0be;</i>

                <a href="https://github.com/Nanookers" target="_blank">
                    <i style='font-size:30px' class='fab' id="gitHub">&#xf092;</i>
                </a>
            </div>
        </div>
    </div>
</template>

<style scoped>
.card{
    display: flex;
  
}
.externalLinks{
    display: flex;
    justify-content: end;
}
.fab, .material-icons{
    cursor: pointer;
    margin-right: 15px;
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

.titles{
    margin-left: 1rem;
    height: 125px;
    width: 450px;
}

.titles h1{
    margin-bottom: 10px;
    margin-top: 10px;
}

.titles h3{
    margin: 0;
    padding: 0;
}
.titles p{
    margin: 0;
    padding-top: 8px ;
}
svg{
    width: 100px;
    height: 100px;
}

</style>
