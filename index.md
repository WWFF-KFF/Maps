## Welcome to GitHub Pages

<!DOCTYPE html>
<html>
  <head>
  <style>
    #map-canvas { width:600px; height:600px; }
    .layer-wizard-search-label { font-family: sans-serif };
  </style>
  <script type="text/javascript"
    src="http://maps.google.com/maps/api/js?sensor=false">
  </script>
  <script type="text/javascript">
    var map;
    var layer_0;
    function initialize() {
      map = new google.maps.Map(document.getElementById('map-canvas'), {
        center: new google.maps.LatLng(36.52493934935506, -109.00346708984375),
        zoom: 3,
        mapTypeId: google.maps.MapTypeId.ROADMAP
      });
      layer_0 = new google.maps.FusionTablesLayer({
        query: {
          select: "col5",
          from: "13FFZugovlAfn6cbQgw2EXjWPmxz2ifqYEtPT7hEx"
        },
        map: map,
        styleId: 2,
        templateId: 2
      });
    }
    function changeMap_0() {
      var whereClause;
      var searchString = document.getElementById('search-string_0').value.replace(/'/g, "\\'");
      if (searchString != '--Select--') {
        whereClause = "'reference' CONTAINS IGNORING CASE '" + searchString + "'";
      }
      layer_0.setOptions({
        query: {
          select: "col5",
          from: "13FFZugovlAfn6cbQgw2EXjWPmxz2ifqYEtPT7hEx",
          where: whereClause
        }
      });
    }
    google.maps.event.addDomListener(window, 'load', initialize);
  </script>
  </head>
  <body>
    <div id="map-canvas"></div>
    <div style="margin-top: 10px;">
      <label class="layer-wizard-search-label">
        Reference
        <input type="text" id="search-string_0">
        <input type="button" onclick="changeMap_0()" value="Search">
      </label> 
    </div>
  </body>
</html>
