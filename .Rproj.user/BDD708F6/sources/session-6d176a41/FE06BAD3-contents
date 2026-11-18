library(shiny)
load("tenMileRace.rda")

# Define UI for application that draws a histogram
ui <- fluidPage(
  
  # Application title
  titlePanel("Ten Mile Race Data"),
  
  # Sidebar with a slider input for number of bins 
  sidebarLayout(
    sidebarPanel(
      sliderInput("bins",
                  "Number of bins:",
                  min = 1,
                  max = 50,
                  value = 30),
      sliderInput(
        "limits", "Specify range",
        min = 0, max = 11000,
        value = range(TenMileRace$net)
      ),
    ),
    
    # Show a plot of the generated distribution
    mainPanel(
      plotOutput("distPlot")
    )
  )
)

# Define server logic required to draw a histogram
server <- function(input, output) {
  
  output$distPlot <- renderPlot({
    # generate bins based on input$bins from ui.R
    x    <- TenMileRace$net
    bins <- seq(min(x), max(x), length.out = input$bins + 1)
    
    # draw the histogram with the specified number of bins
    hist(x, breaks = bins, col = 'darkgray', border = 'white',
         xlab = 'Net Completion Time',
         main = 'Histogram of race time')
  })
}

# Run the application 
shinyApp(ui = ui, server = server)

