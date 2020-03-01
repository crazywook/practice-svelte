<div>
  <h1>Corona Patient</h1>
  <label>주소:&nbsp;
    <input
      type="text"
      bind:value={newPatient.address}
    >
  </label>
  <label>이름:&nbsp;
    <input
      type="text"
      on:keypress={handleInputName}
      bind:value={newPatient.name}
    >
  </label>
  <ul>
    {#each patients as patient}
      <li class="patient-info">
        <span class="patient-info__address">{patient.address}</span>
        <span class="patient-info__name">{patient.name}</span>
        <button class="patient-info__delete-btn"
          on:click={createHandleDeletePatient(patient.id)}
        >
          X
        </button>
      </li>
    {/each}
  </ul>
</div>

<script>
import _ from 'lodash'

const newPatient = {
  address: null,
  name: null,
}

let patients = [
  {
    id: 1,
    address: 'yeongdeungpo-gu',
    name: 'mansu',
  },
  {
    id: 2,
    address: 'kwanak-gu',
    name: 'kuwait park',
  },
]

function handleInputName(e) {
  if (e.code.toLowerCase() === 'enter') {
    addPatient(newPatient)
  }
}

function createHandleDeletePatient(id) {
  patients = patients.filter(p => p.id !== id)
}

function addPatient(newPatient) {

  const latestPatient = _.maxBy(patients, 'id')
  const ai = latestPatient.id + 1

  patients = [
    ...patients,
    {
      id: ai,
      address: newPatient.address,
      name: newPatient.name
    }
  ]
}

</script>

<style>
  ul {
    list-style: none;
  }
  label {
    display: inline-block;
  }
  .patient-info {
    margin: 0 auto 0.8rem;
    width: 30rem;
    display: flex;
    align-items: center;
  }
  .patient-info__address {
    flex: 2;
    font-weight: 800;
    font-size: 1.2rem;
    color: dodgerblue;
  }
  .patient-info__name {
    flex: 3;
    font-weight: normal;
    font-size: 1rem;
    color: #2a2a2a;
  }
  .patient-info__delete-btn {
    margin: 0;
    padding: 0;
    border: 0;
    color: #8f8f8f;
    background-color: #fff;
  }
</style>