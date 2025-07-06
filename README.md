library(shiny)

# Define UI for application that draws a histogram
ui <- fluidPage(

    # Application title
    titlePanel("my first Dashboard"),

    # Sidebar with a slider input for number of bins 
    sidebarLayout(
        sidebarPanel(
            sliderInput("num",
                        "Choose a number",
                        min = 1,
                        max = 50,
                        value = 30)
        ),

        # Show a plot of the generated distribution
        mainPanel(
           textOutput("text"),
           plotOutput("plot")
        )
    )
)

# Define server logic required to draw a histogram
server <- function(input, output) {

    output$text <- renderText({
       paste("you selected:", input&num)
    })

    output$plot <- renderPlot({
      hist(rnorm(input$num), col = "skyblue", main = "Historgram")
    })
}
shinyApp(ui = ui, server = server)

