<script>
    import Markimg from "./markimg.svelte";

  let squares =[
    'B','B' ,'B',
    'B','B','B',
    'B','B','B'
  ]
  let initial= "x"
  let actual= initial
  let next = {"x" : "o" , "o" : "x"}

  function handleClick(i) {
    if (squares[i]== ""){
      squares[i] = next[actual];
      actual =  next[actual]
    }
      
  
	}



  let equivalent =  [{
    "XBB|BBB|BBB":"XBB|BBB|BBB",
    "BBX|BBB|BBB":"XBB|BBB|BBB",
    "BBB|BBB|XBB":"XBB|BBB|BBB",
    "BBB|BBB|BBX":"XBB|BBB|BBB",

    "BXB|BBB|BBB":"BXB|BBB|BBB",
    "BBB|XBB|BBB":"BXB|BBB|BBB",
    "BBB|BBX|BBB":"BXB|BBB|BBB",
    "BBB|BBB|BXB":"BXB|BBB|BBB",
    
    "BBB|BXB|BBB":"BBB|BXB|BBB",
  },

  {
    "XOB|BBB|BBB":"XOB|BBB|BBB",
    "XBB|OBB|BBB":"XOB|BBB|BBB",

    "XBO|BBB|BBB":"XBO|BBB|BBB",
    "XBB|BBB|OBB":"XBB|BBB|BBB",
    
    "XBB|BBO|BBB":"XBB|BBB|BBB",
    "XBB|BBB|BOB":"XBB|BBB|BBB",

    "XBB|BBB|BBO":"XBB|BBB|BBB",

    "XBB|BOB|BBB":"XBB|BBB|BBB",
    
//TODO
    "OXB|BBB|BBB":"BXB|BBB|BBB",
    "BXO|BBB|BBB":"BXB|BBB|BBB",
    "BXB|OBB|BBB":"BXB|BBB|BBB",
    "BXB|BOB|BBB":"BXB|BBB|BBB",
    "BXB|BBO|BBB":"BXB|BBB|BBB",
    "BXB|BBB|OBB":"BXB|BBB|BBB",
    "BXB|BBB|BOB":"BXB|BBB|BBB",
    "BXB|BBB|BBO":"BXB|BBB|BBB",


    "OBB|BXB|BBB":"BBB|BXB|BBB",
    "BOB|BXB|BBB":"BBB|BXB|BBB",
    "BBO|BXB|BBB":"BBB|BXB|BBB",
    "BBB|OXB|BBB":"BBB|BXB|BBB",
    "BBB|BXO|BBB":"BBB|BXB|BBB",
    "BBB|BXB|OBB":"BBB|BXB|BBB",
    "BBB|BXB|BOB":"BBB|BXB|BBB",
    "BBB|BXB|BBO":"BBB|BXB|BBB",


  }
];



</script>

<div class="grid" >  
  {#each squares as square , i}
  <div class = "gridmin90" on:click={()=>{handleClick(i)}}  >
    <div class="mark" >
      <Markimg mark={square} />
    </div>
    
  </div>
  {/each}
</div>

<style>
.grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  transition: transform 1s;
}
.mark {
  position: relative;
  background-color: #ccc;

  flex: 0 0 33.333333%;

  display: flex;
  align-items: center;
  justify-content: center;
}
.grid:hover  {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  transform: rotate(90deg);
}

</style>