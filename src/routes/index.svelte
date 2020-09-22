<script>
  // create an empty person object
  let person = {
    firstName: '',
    lastName: '',
    age: '',
  }


  // https://firebase.google.com/docs/firestore/manage-data/add-data#set_a_document
  function savePerson() {
    // save the person object to the database under their first name
    db.collection('people').doc(person.firstName).set(person)
  }


  // https://firebase.google.com/docs/firestore/query-data/get-data#get_a_document
  async function getPerson() {
    // get the document from the database for the given name
    let doc = await db.collection('people').doc(person.firstName).get()

    // get the data from the person document
    person = doc.data()
  }
</script>

<!-- this is just a section to make the page look nice -->
<section class="content section">

  <h1>People</h1>

  <!-- a place to enter the first name -->
  <label>
    First name: <input bind:value={person.firstName}>
  </label>

  <!-- a place to enter the last name -->
  <label>
    Last name: <input bind:value={person.lastName}>
  </label>

  <!-- a place to enter the age -->
  <label>
    Age: <input bind:value={person.age}>
  </label>

  <button on:click={getPerson}>Get Person</button>

  <button on:click={savePerson}>Save Person</button>

</section>

