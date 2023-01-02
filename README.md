<script src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY"></script>
function initMap() {
  // Create the map
  const map = new google.maps.Map(document.getElementById("map"), {
    center: { lat: 0, lng: 0 },
    zoom: 2
  });

  // Create the search form
  const input = document.getElementById("search");
  const searchBox = new google.maps.places.SearchBox(input);
  map.controls[google.maps.ControlPosition.TOP_LEFT].push(input);

  // Add event listener for search form submission
  searchBox.addListener("places_changed", () => {
    const places = searchBox.getPlaces();

    if (places.length == 0) {
      return;
    }

    // Get the first place from the search results
    const place = places[0];

    // Set the map center to the searched place
    map.setCenter(place.geometry.location);
    map.setZoom(12);

    // Add a marker to the map for the searched place
    new google.maps.Marker({
      position: place.geometry.location,
      map: map
    });
  });
}
<body onload="initMap()">
  <!-- Your HTML code here -->
</body>
