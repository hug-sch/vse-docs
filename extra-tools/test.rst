test
----

testing ...


.. raw:: html
 
   <style>
      #layer2, #layer3 {
         visibility: hidden;
      }
   </style>

   <svg id="svg" width="920" height="360"></svg>
   
   <button onClick=toggleDisplay(layer1)>toggle layer1</button>
   <button onClick=toggleDisplay(layer2)>toggle layer2</button>
   <button onClick=toggleDisplay(layer3)>toggle layer3</button>
  
   <script src="//cdnjs.cloudflare.com/ajax/libs/snap.svg/0.2.0/snap.svg-min.js"></script>

   <script type="application/javascript">

   // This is the Snap.svg object, It's an existing node in our DOM.
   var s1 = Snap("#svg");
   Snap.load("/_static/images/test.svg", function(f) {
      var groups = f.selectAll('g');
    
      // Iterate over each group found
      groups.items.forEach(function(item) {
         
         // GET THE ID
         var id = item.attr("id");
         var displ = item.attr("style")
         //alert("id=" + id + "--- display: " + displ)
      });
      

      s1.append(f);
     
    
   });

   function toggleDisplay(me)
   {
      grps = s1.selectAll('g');
      alert(grps.items(1).id);
     //alert(me.getAttribute("style"));
     if(me.getAttribute("style")=="display:inline")
         me.setAttribute("style","display: none")
      else
         me.setAttribute("style","display:inline")
   }

   </script>
   