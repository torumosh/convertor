<template>
    <Page>
        <ActionBar>
            <Label text="Конвертер"/>
        </ActionBar>
        <StackLayout class="wrapper">
            <FlexboxLayout class="container-menu">
                <Button 
                    class="container-menu__link"
                    @tap="goToPage('/weight')"
                >Масса</Button>
                <Button 
                    class="container-menu__link"
                    @tap="goToPage('/temperature')"
                >Давление</Button>
                <Button 
                    class="container-menu__link"
                    @tap="goToPage('/length')"
                >Длинна</Button>
                <Button 
                    class="container-menu__link"
                    @tap="goToPage('/area')"
                >Площадь</Button>
                <Button 
                    class="container-menu__link"
                    @tap="goToPage('/energy')"
                >Энергия</Button>
            </FlexboxLayout>
        </StackLayout>

    </Page>

</template>

<script>
  export default {
      methods: {
          goToPage(route) {
              this.$navigator.navigate(route)
          }
      },
  };
</script>

<style lang="scss">
.wrapper {
    // background: linear-gradient(to bottom, #ffc9c6 50%, #e0e2ff 50%);
    height: 100%;
    padding-bottom: 2%;
}
Button {
    margin: 0;
    padding: 0;
}
.container-menu {
    margin-top: 40px;
    flex-wrap: wrap;
    justify-content: flex-start;

    &__link {
        color: #525be3;
        background-color: #ffc7c7;
        margin: 0;
        padding: 0;
        width: 100%;
        height: 15%;
        border-radius: 17;
    
        &:active &.tapped {
            color: #ffffff;
        }

    }
}
</style>