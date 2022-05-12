<script>
export default {
    data() {
        return {
            firstValueField: 0,
            firstType: 0,
            secondType: 1,
            resultConvert: 0,
            listUnits: [
                'Квадратный метр',
                'Квадратный см',
            ],
        }
    },
    computed: {
        result() {
            return `= ${this.resultConvert}`
        }
    },
    watch: {
        firstType(newVal) {
            if (newVal === 0) {
                this.secondType === 0 
                    ? this.resultConvert = this.firstValueField
                    : this.resultConvert = this.firstValueField * 10000
            }
            else if (newVal === 1) {
                this.secondType === 0 
                    ? this.resultConvert = this.firstValueField / 10000 
                    : this.resultConvert = this.firstValueField
            }
        },
        secondType(newVal) {
            if (newVal === 0) {
                this.firstType === 0 
                    ? this.resultConvert = this.firstValueField
                    : this.resultConvert = this.firstValueField / 10000
            }
            else if (newVal === 1) {
                this.firstType === 0 
                    ? this.resultConvert = this.firstValueField * 10000 
                    : this.resultConvert = this.firstValueField 
            }
        },
        firstValueField() {
            this.convertSecond()
        },
    },
    methods: {
        convertSecond() {
            if (this.firstType === this.secondType) 
                this.resultConvert = this.firstValueField
            else            
                this.firstType === 1 && this.secondType === 0 
                    ? this.resultConvert = this.firstValueField / 10000
                    : this.resultConvert = this.firstValueField * 10000 
        },
        reverse() {
            const firstValueField = this.firstValueField
            const firstType = this.firstType

            this.firstValueField = this.resultConvert
            this.firstType = this.secondType

            this.resultConvert = firstValueField
            this.secondType = firstType
        }
    },

}
</script>

<template>
    <Page>
      <ActionBar title="Площадь"/>
      <StackLayout verticalAlignment="top">
          <GridLayout columns="*, *" rows="auto, auto">
            <ListPicker 
                class="select-type"
                :items="listUnits" 
                v-model="firstType"
                selectedIndex="0"
                row="0" col="0"
            />
            <ListPicker 
                class="select-type"
                :items="listUnits" 
                v-model="secondType"
                selectedIndex="1"
                row="0" col="1"
            />
        </GridLayout>
        <FlexboxLayout justifyContent="space-around" marginTop="30" >
            <TextField 
                :text="firstValueField" 
                v-model="firstValueField"
                hint="0"
                width="33%"
            />
            <button 
                class="button-transfer"
                @tap="reverse" 
                text="⇆" 
                width="33%"

            />
            <Label 
                marginTop="30"
                :text="result" 
                width="33%"
            ></Label>
        </FlexboxLayout>
        <button 
            @tap="$navigator.back()" 
            text="Назад" 
            marginTop="30"
        />
      </StackLayout>
    </Page>
</template>

<style lang="scss">
    .select-type {
       background-color: rgb(235, 246, 255);
    }
    .result-field {
        color: black
    }
    .button-transfer {
        width: 10%;
        border-radius: 50%;
    }
</style>