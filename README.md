# Layer
SimpleMedia
#include <SDL2/SDL.h>

int main(int argc, char* argv[]) {
    SDL_Window* window = nullptr;
    SDL_Renderer* renderer = nullptr;
    
    SDL_Init(SDL_INIT_VIDEO);
    
    window = SDL_CreateWindow("Drawing on Demand", SDL_WINDOWPOS_CENTERED, SDL_WINDOWPOS_CENTERED, 640, 480, SDL_WINDOW_SHOWN);
    renderer = SDL_CreateRenderer(window, -1, SDL_RENDERER_ACCELERATED);
    
    bool quit = false;
    SDL_Event event;
    
    while (!quit) {
        while (SDL_PollEvent(&event)) {
            if (event.type == SDL_QUIT) {
                quit = true;
            }
        }
        
        SDL_SetRenderDrawColor(renderer, 255, 255, 255, 255); // set background color to white
        SDL_RenderClear(renderer); // clear the screen
        
        // draw a red rectangle
        SDL_Rect rect = { 100, 100, 200, 200 };
        SDL_SetRenderDrawColor(renderer, 255, 0, 0, 255); // set color to red
        SDL_RenderFillRect(renderer, &rect);
        
        SDL_RenderPresent(renderer); // present the renderer to the window
    }
    
    SDL_DestroyRenderer(renderer);
    SDL_DestroyWindow(window);
    
    SDL_Quit();
    
    return 0;
}
