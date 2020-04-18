<template>
  <div>
    <button class="accordion">
      {{ getHospitalNameFromLang() }}
    </button>
    <div class="panel">
      <p>
        <span class="font-weight-bold">Total Treated / Admitted to the hospital:</span> {{ hospital.treatment_total }}
      </p>
      <p>
        <span class="font-weight-bold">Total Tested / Being Tested:</span> {{ hospital.cumulative_total }}
      </p>
      <p class="panel__tel">
        Telephone No: <a class="panel__tel-link" :href="`tel:${getHospitalContactNumber(hospital)}`">{{ getHospitalContactNumber(hospital) }}</a>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Hospital',
  props: {
    hospital: {
      default: () => {
        return null
      },
      type: Object
    },
    language: {
      default: 'name',
      type: String
    }
  },
  data() {
    return {
      telephoneNumbers: [
        {
          hospitalId: 1,
          hospitalTel: '0112 411 224'
        },
        {
          hospitalId: 2,
          hospitalTel: '0112 691 111'
        },
        {
          hospitalId: 3,
          hospitalTel: '0112 959 261'
        },
        {
          hospitalId: 4,
          hospitalTel: '0912 232 267'
        },
        {
          hospitalId: 5,
          hospitalTel: '0252 222 261'
        },
        {
          hospitalId: 6,
          hospitalTel: '0372 222 261'
        },
        {
          hospitalId: 7,
          hospitalTel: '0212 218 101'
        },
        {
          hospitalId: 8,
          hospitalTel: '0812 222 261'
        },
        {
          hospitalId: 9,
          hospitalTel: '0652 222 261'
        },
        {
          hospitalId: 10,
          hospitalTel: '0332 222 261'
        },
        {
          hospitalId: 11,
          hospitalTel: '0312 222 261'
        },
        {
          hospitalId: 12,
          hospitalTel: '0452 222 261'
        },
        {
          hospitalId: 13,
          hospitalTel: '0552 222 261'
        },
        {
          hospitalId: 14,
          hospitalTel: '0112 693 711'
        },
        {
          hospitalId: 15,
          hospitalTel: '0112 662 619'
        },
        {
          hospitalId: 16,
          hospitalTel: '0272 222 261'
        },
        {
          hospitalId: 17,
          hospitalTel: '0112 763 262'
        },
        {
          hospitalId: 18,
          hospitalTel: '0112 695 529'
        },
        {
          hospitalId: 19,
          hospitalTel: '0472 220 261'
        },
        {
          hospitalId: 20,
          hospitalTel: '0552 276 261'
        },
        {
          hospitalId: 21,
          hospitalTel: '0272 259 426'
        },
        {
          hospitalId: 22,
          hospitalTel: '0342 222 261'
        },
        {
          hospitalId: 23,
          hospitalTel: '0112 958 271'
        },
        {
          hospitalId: 24,
          hospitalTel: '0112 578 226'
        },
        {
          hospitalId: 25,
          hospitalTel: '0112 855 200'
        },
        {
          hospitalId: 26,
          hospitalTel: '0112 407 600'
        },
        {
          hospitalId: 27,
          hospitalTel: '0322 223 261'
        },
        {
          hospitalId: 28,
          hospitalTel: '0412 222 261'
        },
        {
          hospitalId: 29,
          hospitalTel: '0112 044 555'
        },
        {
          hospitalId: 30,
          hospitalTel: '0242 222 761'
        },
        {
          hospitalId: 31,
          hospitalTel: '0322 254 261'
        },
        {
          hospitalId: 32,
          hospitalTel: '0112 778 610'
        },
        {
          hospitalId: 33,
          hospitalTel: '0342 276 162'
        }
      ]
    }
  },
  mounted() {
    const acc = document.getElementsByClassName('accordion')
    let i

    for (i = 0; i < acc.length; i++) {
      acc[i].addEventListener('click', function() {
        this.classList.toggle('active')
        const panel = this.nextElementSibling
        if (panel.style.maxHeight) {
          panel.style.maxHeight = null
        } else {
          panel.style.maxHeight = panel.scrollHeight + 'px'
        }
      })
    }
  },
  methods: {
    getHospitalNameFromLang() {
      switch (this.language) {
        case 'name_si':
          return this.hospital.hospital.name_si

        case 'name_ta':
          return this.hospital.hospital.name_ta

        default:
          return this.hospital.hospital.name
      }
    },
    getHospitalContactNumber(hospital) {
      const items = this.telephoneNumbers
      return items.find(item => item.hospitalId === hospital.hospital_id).hospitalTel
    }
  }
}
</script>
