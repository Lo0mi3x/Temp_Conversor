use std::io;
use std::io::stdout;
use std::io::Write;
use std::thread::sleep;
use std::time::Duration;

enum Conv {
    Cels2Farh,
    Farh2Cels,
}

struct ConvCount {
    conv_type : Conv,
    count : i32,
}

fn main() {
    let header = ["Press 1 to convert from Celsius to Fahrenheit","Or 2 to convert from Fahrenheit to Celsius","(press 0 to exit)"];
    intro(header);
    game_on();
    sleeper_print("GOOD BYE!", 130);
}

fn sleeper_print(string: &str, secs: u64) {
    for c in string.chars() {
        print!("{c}");
        stdout().flush().expect("Err");
        sleep(Duration::from_millis(secs));
    }
    println!();
}

fn intro(header: [&str;3]){
    let mut i = 0;
    for w in header.iter() { if i < w.len() { i = w.len() } else { continue }};
    sleeper_print(format!("  {tittle:^i$}", tittle = "TEMPERATURE CONVERSOR").as_str(), 90);
    sleeper_print(format!("|| {sep:^i$} ||", sep = " ~".repeat(i/2)).as_str(), 90);
    for w in header.iter() { sleeper_print(format!("|| {w:^i$} ||").as_str(), 65); }
    sleeper_print(format!("|| {sep:^i$} ||", sep = "-".repeat(i)).as_str(), 90);
}

fn convert_to_fahrenheit() {
    println!("~~Enter the temperture in celsius:");

    let mut petition = String::new();
    io::stdin().read_line(&mut petition).expect("NO INPUT");

    let celsius: f64 = petition.trim().parse().expect("Wrong number");

    let fahrenheit = (1.8 * celsius) + 32.0;
    println!("Fahrenheit: {:.1}", fahrenheit);
}

fn convert_to_celsius() {
    println!("~Enter the temperture in fahrenheit:");

    let mut petition = String::new();
    io::stdin().read_line(&mut petition).expect("NO INPUT");

    let fahrenheit: f64 = petition.trim().parse().expect("Wrong number");

    let celsius = (fahrenheit - 32.0) * 5.0 / 9.0;
    println!("Celsius: {:.1}", celsius);
}

fn count_conversions(conv: ConvCount) {
    match conv.conv_type {
        Conv::Cels2Farh => println!("{:?} conversions from Celsius to Farhenheit", conv.count),
        Conv::Farh2Cels => println!("{:?} conversions from Farhenheit to Celsius", conv.count),
    }    
    println!();
}

fn game_on(){
    let mut celsius_farh = ConvCount {
        conv_type : Conv::Cels2Farh,
        count : 0,
    };
    let mut farhenheit_cels = ConvCount {
        conv_type : Conv::Farh2Cels,
        count : 0,
    };

    loop {
        let mut start = String::new();
        io::stdin().read_line(&mut start).expect("NO INPUT");

        let start: u8 = match start.trim().parse() {
            Ok(num) => num,
            Err(_) => {
                println!("Please enter a number.");
                continue;
            }
        };

        if start == 1 {
            convert_to_fahrenheit();
            celsius_farh.count +=1;
            println!("");
        } else if start == 2 {
            convert_to_celsius();
            farhenheit_cels.count +=1;
            println!("");
        } else if start == 0 {
            println!("");
            break;
        } else {
            println!("Please enter a number between 0 and 2.");
            continue;
        }
    }
    count_conversions(celsius_farh);
    count_conversions(farhenheit_cels);
}
